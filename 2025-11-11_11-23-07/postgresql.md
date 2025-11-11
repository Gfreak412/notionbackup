### `pg_hba.conf` location - `/var/lib/pgsql/data/pg_hba.conf`
- When freshly installed on windows, make sure to add the `C:\Program Files\PostgreSQL\17\bin` to the PATH
### Shell Indicator - 
- `postgres=#` : this means it ready for a new fresh command
- `postgres-#` : this means the last command did not finish, as `;` was not used
### Shell Commands - 
- `\l` - lists all the databases if used in `postgres` (root console)
- `\dt` - lists all the tables in the database
- `\d table_name` - shows the columns of a table and details of the datatype
- `\i schema.sql` -  include a file
-    ` \copy my_table FROM '/home/user/data/my_data.csv' DELIMITER ',' CSV HEADER;` - import data from csv into a table
<br/>
### Basic Commands
- enter root console - `psql -U postgres -d postgres`
- create a user - `CREATE USER kanishk WITH PASSWORD 'kanishk’;`
- Create a database named <u>*financials*</u>* *with owner `<u>*kanishk*</u>`*- * `CREATE DATABASE financials WITH OWNER kanishk;`
- Change owner of db - `ALTER DATABASE "SIH-2025" OWNER TO kanishk;`
- delete a database - `DROP DATABASE IF EXISTS financials;`
- create a database with a special character in name - `CREATE DATABASE "SIH-2025" WITH OWNER kanishk;`
### Demo Schema 
```sql
-- Optional: schema namespace (dialect-dependent)
-- CREATE SCHEMA app; -- then prefix tables with app.
-- Reference table for FK demo
CREATE TABLE ref_category (
category_id      INTEGER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
code             VARCHAR(32) NOT NULL UNIQUE,
name             VARCHAR(100) NOT NULL,
created_at       TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);
-- Main demo table covering common data types and constraints
CREATE TABLE demo_entity (
-- Identity / keys
id                   INTEGER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
external_uuid        CHAR(36),                            -- store canonical UUID text like XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
-- Strings
username             VARCHAR(100) NOT NULL UNIQUE,        -- variable-width string
display_name         VARCHAR(200),                        -- nullable text
initials             CHAR(2),                             -- fixed-width string
notes                VARCHAR(2000),                       -- longer text; use TEXT/CLOB if supported by engine
-- Unicode (portable aliasing via NATIONAL CHARACTER types)
nshort               NCHAR(10),                           -- fixed-width unicode
ntext                NVARCHAR(400),                       -- variable-width unicode
-- Numbers
tiny_count           SMALLINT CHECK (tiny_count BETWEEN -32768 AND 32767),  -- small integer class
qty                  INTEGER NOT NULL DEFAULT 0,          -- standard integer
big_total            BIGINT,                              -- large integer
exact_amount         DECIMAL(18,4) NOT NULL DEFAULT 0,    -- exact numeric/decimal
approx_ratio         REAL,                                -- approximate float
precise_metric       DOUBLE PRECISION,                    -- higher-precision float
-- Boolean / bit
is_active            BOOLEAN NOT NULL DEFAULT TRUE,       -- BOOLEAN is ANSI; map to BIT/TINYINT(1) where needed
bit_flag             BIT,                                 -- single bit (0/1); some engines use BIT(1)
-- Date/time
d_only               DATE,                                -- date only
t_only               TIME,                                -- time only
occurred_at          TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,  -- timestamp
-- Time zone aware (if supported; else leave as TIMESTAMP)
-- occurred_at_tz    TIMESTAMP WITH TIME ZONE,
-- Binary
fingerprint_sha1     BINARY(20),                          -- fixed-length binary (e.g., SHA-1 bytes)
payload              VARBINARY(1024),                     -- variable-length binary
-- JSON / XML (portable placeholders; enable per engine)
-- json_data         JSON,                                -- PostgreSQL/MySQL
-- xml_data          XML,                                 -- PostgreSQL/SQL Server
-- Money (exact numeric preferred; some engines have MONEY)
-- price             MONEY,
-- Enumerations via CHECK
status               VARCHAR(20) NOT NULL
CHECK (status IN ('new','active','suspended','deleted')),
-- Foreign key
category_id          INTEGER REFERENCES ref_category(category_id),
-- Generated/computed example (portable expression; exact syntax may vary)
full_label           VARCHAR(320)
GENERATED ALWAYS AS
(COALESCE(display_name, username)) STORED,
-- Defaults and additional checks
created_at           TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
updated_at           TIMESTAMP,
CONSTRAINT chk_amount_nonnegative CHECK (exact_amount >= 0),
CONSTRAINT uq_uuid UNIQUE (external_uuid),
CONSTRAINT uq_category_username UNIQUE (category_id, username)
);
-- Indexes (beyond PK/UNIQUE)
CREATE INDEX idx_demo_entity_status ON demo_entity (status);
CREATE INDEX idx_demo_entity_occurred_at ON demo_entity (occurred_at);
-- Trigger or automatic update of updated_at (dialect-specific; example shown in portable pseudocode)
-- PostgreSQL example:
-- CREATE OR REPLACE FUNCTION set_updated_at() RETURNS trigger AS $$
-- BEGIN NEW.updated_at = CURRENT_TIMESTAMP; RETURN NEW; END $$ LANGUAGE plpgsql;
-- CREATE TRIGGER trg_demo_entity_updated BEFORE UPDATE ON demo_entity
-- FOR EACH ROW EXECUTE FUNCTION set_updated_at();
-- Seed example
INSERT INTO ref_category (code, name) VALUES
('GEN', 'General'),
('VIP', 'VIP');
INSERT INTO demo_entity (external_uuid, username, display_name, initials, nshort, ntext,
tiny_count, qty, big_total, exact_amount, approx_ratio, precise_metric,
is_active, bit_flag, d_only, t_only, status, category_id,
fingerprint_sha1, payload)
VALUES
('550e8400-e29b-41d4-a716-446655440000', 'alice', 'Alice A.', 'AA', N'ユーザ', N'こんにちは',
10, 100, 1234567890123, 12.3400, 0.125, 3.14159265358979,
TRUE, B'1', DATE '2025-09-02', TIME '10:30:00', 'active', 1,
x'DA39A3EE5E6B4B0D3255BFEF95601890EDD', x'DEADBEEF');
```
