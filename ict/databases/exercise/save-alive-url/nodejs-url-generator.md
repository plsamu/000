# NodeJS - URL generator

Will generate only .it URL using words taken from a txt books.

<details>

<summary>How do I select a record from a database only once?</summary>

[https://stackoverflow.com/questions/14419177/how-to-select-a-random-record-from-database-only-once](https://stackoverflow.com/questions/14419177/how-to-select-a-random-record-from-database-only-once)

Mmmmmh... Maybe just select all then consume the collection one by one...

```
// PSEUDOCODE
records = getAllRecords()
url = array<string>
while(records.length != 0) {
    r = random() * records.length
    element = records.get(r)
    url.add(generateUrl(element))
    records.remove(r) // do this work inside a while? 
}
```

</details>
