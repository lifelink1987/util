# Life-Link Friendschip-Schools utility belt

## bin/dump_contacts

Extract email addresses from the database,
split in groups of maximum N (N<400) addresses,
into JSON, email or CSV format (for mailchimp)

```json
[
  [{
    "name": "",
    "email": "",
    "country": ""
  }]
, [{...}]
]
```

```
name1 <email1>,
name2 <email2>,
...
```

```
name1 email1 country1
name3 email2 country2
```


## License

[UNLICENSE](LICENSE)
