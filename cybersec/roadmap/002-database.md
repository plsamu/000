# 002 - Database

This is tricky.

Sometime a database is needed to organize all the informations.

* NoSQL or SQL ?

Sometime is needed just a text file to open it fastly.&#x20;

* e.g. [https://github.com/duyet/bruteforce-database](https://github.com/duyet/bruteforce-database)

{% embed url="https://stackoverflow.com/questions/38120895/database-vs-file-system-storage" %}

{% embed url="https://stackoverflow.com/questions/8381916/sql-text-field-vs-flat-file-vs-nosql-document-store" %}

## Questions

<details>

<summary>Do I need to index the contents of a txt file?</summary>

Yes? Use a database.

</details>

<details>

<summary>Isn't the database slower?</summary>

I will be able to give more complete answers in the future, BUT.

As you open a file for example with:

```javascript
fs.readFile('words.txt', (err, data) => console.log(data))
```

You can also just:

```sql
SELECT * from words
```

</details>
