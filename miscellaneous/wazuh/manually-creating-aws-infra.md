# Manually creating aws infra

Create two instance

1. wazuh-server
2. wazuh-agent



**wazuh-agent**

```
aws ec2 create-security-group --group-name "launch-wizard-2" --description "launch-wizard-2 created 2024-12-28T06:38:29.241Z" --vpc-id "vpc-0a7d795e972934dc7" 
aws ec2 authorize-security-group-ingress --group-id "sg-preview-1" --ip-permissions '{"IpProtocol":"tcp","FromPort":22,"ToPort":22,"IpRanges":[{"CidrIp":"0.0.0.0/0"}]}' 
aws ec2 run-instances --image-id "ami-0e2c8caa4b6378d8c" --instance-type "t3.micro" --block-device-mappings '{"DeviceName":"/dev/sda1","Ebs":{"Encrypted":false,"DeleteOnTermination":true,"Iops":3000,"SnapshotId":"snap-0ea137085731e5c98","VolumeSize":20,"VolumeType":"gp3","Throughput":125}}' --network-interfaces '{"AssociatePublicIpAddress":true,"DeviceIndex":0,"Groups":["sg-preview-1"]}' --credit-specification '{"CpuCredits":"unlimited"}' --tag-specifications '{"ResourceType":"instance","Tags":[{"Key":"Name","Value":"wazuh-agent"}]}' --metadata-options '{"HttpEndpoint":"enabled","HttpPutResponseHopLimit":2,"HttpTokens":"required"}' --private-dns-name-options '{"HostnameType":"ip-name","EnableResourceNameDnsARecord":true,"EnableResourceNameDnsAAAARecord":false}' --count "1" 
```

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

* Proper security group rules:
  * Wazuh manager requires ports 22  and 1514.
  * Wazuh agent requires port 1514 to communicate with the manager.

<figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

