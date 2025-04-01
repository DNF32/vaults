---
aliases:
  - foreign key
tags:
  - delete-cascade
  - update-no-action
title: foreign-key
---

# foreign key

```SQL
CREATE TABLE country_languages (
	country_id INTEGER NOT NULL,
	language_id INTEGER NOT NULL,
	PRIMARY KEY (country_id, language_id),
	FOREIGN KEY (country_id) REFERENCES countries (country_id)
            ON DELETE CASCADE ON UPDATE NO ACTION,
	FOREIGN KEY (language_id) REFERENCES languages (language_id)
            ON DELETE CASCADE ON UPDATE NO ACTION
);
```

We define a table with two interger columns, country_id and language_id, which in combination we define them as a `primary key`.

```SQL
FOREIGN KEY (country_id) REFERENCES countries (country_id)
```

Tells us that we have foreign key constrain (i.e this element is a primary key in another table), and tells us in which table is it.
The `ON DELETE CASCADE` means that if we delete country_id from it's primary key table we cascade this deletion to this table, i.e, every record that uses that id will be removed.
`ON UPDATE NO ACTION ` means that if we try to update the country_id in it's PK table and the system finds that there are records in this table that have the pre change id, the system won't allow the update.

Basiclly the system won't allow changes that break referencial intengrity.
