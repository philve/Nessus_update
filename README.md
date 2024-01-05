# Nessus_update

It is mainly a wheel created to solve the headache of some big guys trying to find all-2.0.tar.gz of nessus.
![image](https://user-images.githubusercontent.com/14137698/82754925-d2ae8f80-9e02-11ea-89d1-293549d14fe7.png)

```
python get_activ_code.py
```

```
Created email address: g8orwvd0e@getnada.com
Start receiving Nessus registration forms
The obtained Nessus registration password is dchn8Fcnky6mLc5dGDDMHRxu0U6ZyenOT6+Ky0d7rUo=
Registration is successful, please contact g8orwvd0e@getnada.com for relevant information.
You have to wait a while (15 seconds), and there is a certain delay waiting for the mailbox to receive the message.
Get g8orwvd0e@getnada.com email content uid: yqu6hlX4b8c5N3fwuqDUxOpTXkcHoA
Nessus activation code: 1E12-AB04-8DDB-564C-F119
Download address of nessus plugin package: https://plugins.nessus.org/v2/nessus.php?f=all-2.0.tar.gz&u=501b33370d5649f73e029b246eedc3fe&p=1b1ec8c81448c67a986cd397232acb1b
```

Reference about running under Docker [Running nessus under Docker](https://github.com/0xa-saline/Nessus_update/blob/master/Docker.md)

some tips

```
service nessusd stop
# curl  https://www.tenable.com/downloads/api/v1/public/pages/nessus/downloads/10204/download?i_agree_to_tenable_license_agreement=true -o nessus880.deb
# dpkg -i nessus880.deb
# mv /opt/nessus/var/nessus/templates/metadata.json /opt/nessus/var/nessus/templates/metadata.json.old1
# mv /opt/nessus/var/nessus/templates/tmp/metadata.json /opt/nessus/var/nessus/templates/tmp/metadata.json.old1

/opt/nessus/sbin/nessuscli update  /root/all-2.0.tar.gz
# just for first update all-2.0.tar.gz
# cp /opt/nessus/var/nessus/www/policy_wizards.json /opt/nessus/var/nessus/www/policy_wizards.json.bak
# sed -i '/subscription_only": true,/d' /opt/nessus/var/nessus/www/policy_wizards.json
# sed -i '/"manager_only": true,/d' /opt/nessus/var/nessus/www/policy_wizards.json
# sed -i 's/"HomeFeed (Non-commercial use only)"/"ProfessionalFeed (Direct)"/g' /opt/nessus/var/nessus/plugin_feed_info.inc
# sed -i 's/"HomeFeed (Non-commercial use only)"/"ProfessionalFeed (Direct)"/g' /opt/nessus/lib/nessus/plugins/plugin_feed_info.inc
# sed -i 's/Nessus Home/Nessus/g' /opt/nessus/lib/nessus/plugins/scan_info.nasl
# cp /opt/nessus/etc/nessus/nessus-fetch.db.bak /opt/nessus/etc/nessus/nessus-fetch.db
service nessusd start
```
