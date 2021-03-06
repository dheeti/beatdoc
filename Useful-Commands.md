Start Jingoo

```
jingo -c /home/jayram/beat/documents/jingo/config.yaml
```
Reset Mirth Admin Password in Derby DB
```
*connect 'jdbc:derby:/home/jayram/apps/mirthconnect/appdata/mirthdb';*
*update person_password set password='YzKZIAnbQ5m+3llggrZvNtf5fg69yX7pAplfYg0Dngn/fESH93OktQ==' WHERE person_id=1;*
```

Import Bundle
```
rake bundle:import[/home/jayram/beat/bundle-latest-0220.zip,false,false,*,false,true] RAILS_ENV=development
```

Import Patients
```
rake import:patients[/home/jayram/beat/bundledata/patients/ep/json/,true]
```

Run Measure Job
```
rake jobs:work
```

Cleanup mongodb before importing bundles

```
db.system.js.remove();

db.getCollectionNames().forEach(function(c){
    if( (c != 'system.indexes') && (c != 'users') &&(c != 'system.js')){
    print(c)
    db.getCollection(c).drop();    
    }
})
```

Export Mongo Objects in json format
```
mongoexport --db bonnie_development --collection draft_measures --jsonArray --out /home/jayram/beat/testdata/patientjson.json
```

Make AWS based Mongodb accessible throug port 27017

- Make sure you have commented out bind_ip from the mongodb.conf

Chef command to install popHealth on AWS Instance
```
bundle exec knife solo bootstrap 52.11.106.36 --ssh-user ubuntu --identity-file /home/jayram/beat/keys/testPop.pem -r role[popHealth]
```

Command to format XML files in Batch
```
for i in *.xml; do xmllint --format "$i" > ./formated/"$i"; done
```