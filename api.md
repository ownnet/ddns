## API
#### getip
��ȡ��������IP���������
#### gettime
��ȡ������ʱ��������ڱ�����֤��Ϣ������������е���Ƶ������
#### getuserinfo
��ȡ�û���Ϣ������Ϊtoken=�û���½ʱ���ص�token
#### getdomaininfo
��ȡָ��������Ϣ������Ϊtoken=�û���½ʱ���ص�token&domian=sample.com
#### getauthcode
����ȡָ��������Ϣ�е�auth_code�ֶΣ�����ͬgetdomaininfo
#### getdomainlist
��ȡ�û���ӵ�е���������������Ϊtoken=�û���½ʱ���ص�token
#### update
��������ύָ��������ָ���ip��ͨ��get����version���ֲ�ͬ�ķ�ʽ
#####��1��version=safe
`http://yourdomain.com/api/update?version=safe`
post����Ϊauth=ʱ����֤�룻ip=��ǰ��������IP  ��domain=����  
ʱ����֤���ͨ��getauthcode��ʽ��ȡauth_code������ʱ�������ȡ��
����ֵ��(string)'success'|(json)error_info
#####��2��version=username
`http://yourdomain.com/api/update?version=username&domain=����&ip=����ip&username=�û���&password=����`
����get������domain=__HOSTNAME__&ip=__MYIP__&user=__USERNAME__&password=__PASSWORD__
����ֵ��(string)'success'|(json)error_info
���÷�����й¶�û���������գ����ã�
#####��3��version=authcode
`http://yourdomain.com/api/update?version=authcode&auth=auth_code&domain=����&ip=����ip`
����get������auth=auth_code; domain=������ip=����ip
����ֵ��(string)'success'|(json)error_info
���÷�����й¶��ǰ������֤��Ϣ�ķ��գ�

#### auth
�������post��ʽ�ύ�û���/����  
����Ϊuser=xxx;password=xxx
����ֵ��(string)'err'|token_code
#### keepalive
�������������������post��ʽ������Ϊtoken=�û�token  

## ����˵��
#### auth_code ����
MD5��'auth' + time + rand(10000,99999))
#### ʱ����֤����㷽��
ʱ����֤����㷽�����£�
1. �ͻ�������ʱ���ӷ�������ȡ��������ʱ������뱾��ʱ�������¼��ʱ��ƫ����
2. ���������ʱ��time=����ʱ��+ʱ��ƫ����
3. ������֤��Ϣ��auth = md5((int)time/30 + (string)auth_code)
4. �������post��Ϣ�����������ֶΣ�auth,domain,ip���������˽�����ࣩ����ύʱ��ǰ/��1��ʱ��Ƭ��authֵ
5. ���ݷ���ֵ�ظ���2~4���򷵻ش�����Ϣ

