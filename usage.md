# ʹ�÷���
## ����NSServer
���ownnet/ddns_nsserver�ֿ�
## ����WebServer
���ownnet/ddns_webserver�ֿ�
## ���ؿͻ��˰�װ
���ownnet/ddns_client_py�ֿ�
## ����
### ���NS��¼
�����������̵�dns����������һ��NS��¼����������Ϊ��Ҫ�����Ķ����������ƣ�������������������������Խ�NS�������������˴���@����ָ����д���и�NS��������������ip������  
![DDNS1](images/ddns_server_1.jpg)
��¼��Ч�����ж�ddns.yourserver.com���������������ķ��ʣ���������yourserver.com�����е�NS������������  
�����Ҫ������yourserver.comȫ�����ɸ÷�������ֱ���޸����������NS��¼
### ��̨����
����ɲ��������http://your.webdomain.com/ ��½��Ĭ�����ݿ�������һ���û��������Ϊamin���û������ڵ�һʱ���޸�����
�������˵�-��������-�������������һ������������༶����������������¼����д����������������home.ddns.yourserver.com����¼ֵ���գ������ύ��
��/domain/list�У���������-�����б��в鿴��ǰ����(����home.ddns.imgroot.bidΪ��)
![domain/list](images/domain_list.jpg)

### ʹ�ÿͻ���
���ַ�����  
1. Ĭ�ϵ�safeģʽ  
`python3 console.py -1 -t safe -d home.ddns.imgroot.bid -c f77c28d33cfc83408332e058da0b5040`  
2. �û�������ģʽ  
`python3 console.py -1 -t username -d home.ddns.imgroot.bid -u admin -p admin`  
3. ������Ȩ��ģʽ  
`python3 console.py -1 -t authcode -d home.ddns.imgroot.bid -c f77c28d33cfc83408332e058da0b5040`

�����ʹ��Ⱥ�ͣ���ο��ĵ�02 [��Ⱥ����ʹ��](./use_in_Synology.md)