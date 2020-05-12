---
title: python script teamcymru (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'teamcymru'

Functions in program: 
* `def teamcymru_ip2asn_bulk(pandaseries_ips):`
* `def teamcymru_ip2asn (ip):`

Modules used in program: 
* `import pandas as pd`
* `import time`
* `import random`
* `import os.path`
* `import subprocess`
* `import time`
* `import random`
* `import os.path`
* `import subprocess`

## python teamcymru

Python mysql example: teamcymru

```python
###INSTALL: netcat or gnetcat (NOT nc)

import subprocess
import os.path
import random
import time
impott pandas as pd

def teamcymru_ip2asn (ip):
    command = 'whois -h whois.cymru.com " -v ' + ip + '"'
    output,error = subprocess.Popen(command, universal_newlines=True, shell=True, stdout=PIPE, stderr=PIPE).communicate()
    return output

import subprocess
import os.path
import random
import time
import pandas as pd

def teamcymru_ip2asn_bulk(pandaseries_ips):
    iptoasn_response = open('output_ip2asn_teamcymru.txt', 'w')

    #Creating the request file containing a list of IPs
    #For more information, please access: http://www.team-cymru.com/IP-ASN-mapping.html
    iptoasn_request = open('input_ip2asn_teamcymru.txt', 'w')
    iptoasn_request.write('begin\nverbose\n')
    pd.Series(pandaseries_ips.dropna().unique()).to_csv(iptoasn_request,header=False,index=False,sep="\t") 
    iptoasn_request.write('end')
    iptoasn_request.close()

    #Performing the bulk request
    cat = subprocess.Popen(['cat', 'input_ip2asn_teamcymru.txt'], stdout=subprocess.PIPE)
    print(cat)
    netcat = subprocess.Popen(['netcat', 'whois.cymru.com', '43'], stdin=cat.stdout, stdout=iptoasn_response)
    print((netcat))
    time.sleep(3) #for some reason the poll does not work! This was the way to overcome the waiting time.
    #Closing the output file
    iptoasn_response.close()

    df = pd.read_csv('output_ip2asn_teamcymru.txt',\
                     skiprows=1,\
                     delimiter="\s+\|\s",\
                     names = ['asn', 'ip', 'bgp_prefix', 'country','registry','info_date','as_name'])

    ### CAN BE USEFUL: 
    ###df['asn'] = df['asn'].astype(str).apply(lambda x: 'AS'+x.split('.')[0])
    
    !rm input_ip2asn_teamcymru.txt
    !rm output_ip2asn_teamcymru.txt
    
    return df

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
