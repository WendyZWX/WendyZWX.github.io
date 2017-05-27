#hexo+github��ɶ��豸ͬ���Ĳ���#
������Ҫ���ú�node.js��git���������������¼�⣺
```
node --version
```
```
git --version
```
���������ͼ��ʾ��


##1. hexo�İ�װ���������ü�����##
�������hexo�İ�װ���������á�
1. ִ��```npm install -g hexo-cli```�����װhexo���������½������ʾhexo��װ�ɹ�

����```hexo --version```�����⣬��������£�

2. �½��ļ���hexo,������ļ��У��ڸ��ļ����ڴ�git bash����ڣ�ִ��```hexo init```���hexo����Զ���Ŀ���ļ��н�����վ����Ҫ���ļ���������ͼ��ʾ�����ʾ�������

����```npm install```����hexo�ļ����а�װnode_modules��
3. �������ط�����
����```hexo s```�������ط��������������½������hexo server�Ѿ������ˣ���������д�  http://localhost:4000/  ����ʱ���Կ���Hexo��Ϊ��������һƪblog��
����԰�Ctrl+C ֹͣServer��

ע�⣺���������ͼ����� http://localhost:4000/  ʼ���޷��򿪣����Ƕ˿ں�4000��ռ���ˣ�ִ��```hexo s -p 5000```�޸Ķ˿ںţ���ʱ����ַ http://localhost:5000/ �������½����ʾ���ز��ʹ�ɹ��ˡ�

4. ����Github��
����Githubǰ��Ҫ����_config.yml�ļ����޸���������
```
deploy:
  type: github
  repository: git@github.com:zhchnchn/zhchnchn.github.io.git
  branch: master
```
����SSH keys����Git Bash������ָ��```ls -al ~/.ssh```������Ƿ��Ѿ�����SSH keys������ڵĻ�ֱ��ɾ��.ssh�ļ������������ļ���

 ����ָ��
```ssh-keygen -t rsa -C "1413774769@qq.com"```�س�����ʾ����passphrase��Ϊ�˷��㽨��ֱ�ӻس�

Ȼ�����ָ��```ssh-agent -s```

 ��������ָ��```ssh-add ~/.ssh/id_rsa```

������ͼ��ʾ�������������ָ��
```
eval `ssh-agent -s` 
ssh-add
```
 
 ��SSH key��ӵ�Github�˻��ϡ���.ssh�ļ����е�id_rsa.pub�ļ�������ȫ�����ݣ�Ȼ����Github�е��Settings

 ѡ�����ĵ���������Ƶ�id_rsa.pub�ļ�����ճ����Key�ı�����
 ���add key���������Github���뼴�����SSH Key����ӡ���������```ssh -T git@github.com```���ԣ�����о��棬���롰yes�����ɡ�

������ͼ�ṹ����ssh key���óɹ�

ִ��```hexo g```ָ���```hexo d```ָ����ɲ��𣬳�����������

 ʱ��Ҫִ��ָ��```npm install hexo-deployer-git --save```��װ��Ӧ�Ĳ����

 ������ͼ��ʾ�����ʾGithub�ϵĲ�������ˣ���ʱ���ʹ�ɹ�������������� https://WendyZWX.github.io �������½����������˲�����Github�ϵĲ���

 

##2. ���ʵ�ֶ��豸ͬ��hexo�Github����##
��Github�ֿ��master��֧���������ϴ��Ĳ����ļ�����������ļ��ǲ���������Ŷ���õġ�Ҫʵ�ֶ��豸ͬ��hexo�Github���ͣ�������Ҫ�½���֧���˴������½���֧hexo��Ȼ��ʹ��git�������Ŷ���õ�Github�����ļ��ϴ����½��ķ�֧��

 �ڱ��ز��͸�Ŀ¼�£������м�ָhexo�ļ��У�ʹ��gitָ���ϴ���Ŀ��Github��
```
git init
git remote add origin https://github.com/�û���/�ֿ���.git
git checkout -b hexo//hexoΪ�½��ķ�֧��
git add --all
git commit -m "add hexo"
git push origin hexo
```
**ע��**���˴����ǿ��ܳ��ֱ���
- ��ִ��```git add --all```ʱ�����hexo�ļ����е��ļ�����ȫ����ӣ���ʱʹ��```git add --all -f```��hexo��ȫ������ǿ����ӽ�ȥ��
- ��ִ��```git push origin hexo```����ʱ���������ͼ��ʾ����

��ʱ��Ҫ��ִ��```git pull origin hexo```�����ִ��```git push -u origin hexo```���������*packet_write_wait: Connection to ������ port 22: Broken pipe*������������Ӧ��ʱ�������²�����ӻ��޸��ļ����ɣ��ײ���С�
-  ~����ssh�ļ��У������SSH key���ļ��У����½�config�ļ���ע�ⲻҪ����κκ�׺��������config�ļ��������������
```
Host *
	ServerAliveInterval 180
	ServerAliveCountMax 5
```
- �ҵ�Git�İ�װĿ¼���ҵ�/etc/ssh/sshd_config�ļ��������к��������������
```
ClientAliveInterval 60
ClientAliveCountMax	5
```
��/etc/ssh/ssh_config�ļ��������������������
```
TCPKeepAlive yes
```
��ʱִ��```git push -u origin hexo -f```ǿ�ƣ����ɽ�����hexo�ļ�ͬ����hexo��֧��ȥ��

�������豸��clone��Github���½���hexo��֧�е��ļ������أ�����һ̨�豸�ϾͿ���ʹ���ڱ��ر༭���Ͳ�ͬ����Github���ˡ�
```
// ��¡�ļ�������
git clone -b ��֧�� https://github.com/�û���/�ֿ���.git
```

