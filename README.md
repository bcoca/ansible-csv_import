Simple role that maps a matching row in a CSV file to host variables

Use ``` ansible-doc -t role <role name>``` for docs.

Example:

play.yml
```
- hosts: localhost
  gather_facts: false
  vars:
    csv_file_name: testing.csv
  tasks:
    - import_role: name=csv_import
      vars:
        csv_search_term: '127.0.0.1'
```

csv file 'testing.csv'
```
ip,net,mask,noword,her,him,second
127.0.0.1,10.0.0.1,24,nones,lola,pepe,127.0.0.2
128.0.0.1,10.1.0.1,20,notes,lolita,pepito,128.0.0.2
129.0.0.1,10.2.0.1,23,nines,aayush,pepete,129.0.0.2

```

created variables:
```
    "new_variables": {
        "ip": "127.0.0.1"
        "net": "10.0.0.1"
        "mask": "24"
        "noword": "nones"
        "her": "lola"
        "him": "pepe"
        "second": "127.0.0.2"
    },
```
