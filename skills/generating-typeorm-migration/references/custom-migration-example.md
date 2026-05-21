# Custom Migration Examples

Use these examples when you need to create a hand-written migration because TypeORM cannot represent the required database object in entity metadata.

## Office geom expression index

- Entity field: `office.geom`
- Migration: `1778692242502-add-office-geom-2056-active-gist-index.ts`
- Database object: partial GiST expression index on `ST_Transform(geom, 2056)`

```sql
CREATE INDEX idx_office_geom_2056_active_gist
ON office
USING GIST (ST_Transform(geom, 2056))
WHERE verified = true
  AND archived = false
  AND deleted = false
  AND geom IS NOT NULL;
```

## Why this is hand-written

This TypeORM version can model normal indexes on entity columns and supports options such as `spatial` and `where`, but it cannot declare an index on a SQL expression like `ST_Transform(geom, 2056)`.

Because of that:

1. Keep `geom` as the real entity column.
2. Do not add helper or generated columns just to force migration generation.
3. Create the migration with `npm run migration:api:create --name=add-office-geom-2056-active-gist-index`.
4. Write the minimal `up()` / `down()` SQL by hand.
5. Leave a short entity comment that points to the migration and explains why the index is custom.

## Example entity comment

```ts
/**
 * Custom DB indexes:
 * - Office active geom GiST expression index on ST_Transform(geom, 2056)
 *   is created in migration 1778692242502 because TypeORM cannot declare
 *   expression indexes in entity metadata
 */
```

## Office geom sync trigger

- Entity fields: `office.latitude`, `office.longitude`, `office.geom`
- Migration: `1777985073003-add-office-geom-sync-trigger.ts`
- Database object: Postgres trigger plus trigger function that keeps `geom` in sync with coordinates

```sql
CREATE OR REPLACE FUNCTION sync_office_geom_from_coordinates() RETURNS TRIGGER AS $$
BEGIN
  IF NEW.latitude IS NULL OR NEW.longitude IS NULL THEN
    NEW.geom := NULL;
  ELSE
    NEW.geom := ST_SetSRID(ST_Point(NEW.longitude, NEW.latitude), 4326);
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER office_geom_from_coordinates_trigger
BEFORE INSERT OR UPDATE OF latitude, longitude ON office
FOR EACH ROW
EXECUTE FUNCTION sync_office_geom_from_coordinates();
```

## Why this is hand-written

This TypeORM version can model columns and indexes, but it cannot declare Postgres trigger functions and triggers in entity metadata.

Because of that:

1. Keep `latitude`, `longitude`, and `geom` as the real entity fields.
2. Document the trigger in the entity-level DB notes.
3. Create the migration with `npm run migration:api:create --name=add-office-geom-sync-trigger`.
4. Write the minimal `up()` / `down()` SQL by hand.

## Example entity comment

```ts
/**
 * Custom DB triggers:
 * - Office geom sync trigger: automatically updates the "geom" column (Point)
 *   whenever "latitude" or "longitude" are inserted or updated
 *   (migration: 1777985073003)
 */
```
