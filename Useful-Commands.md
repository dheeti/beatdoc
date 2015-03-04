Start Jingoo

```
jingo -c /home/jayram/beat/documents/jingo/config.yaml
```
Reset Mirth Admin Password in Derby DB

'''sql
connect 'jdbc:derby:/home/jayram/apps/mirthconnect/appdata/mirthdb';
update person_password set password='YzKZIAnbQ5m+3llggrZvNtf5fg69yX7pAplfYg0Dngn/fESH93OktQ==' WHERE person_id=1;
'''