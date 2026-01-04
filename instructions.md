gcloud compute instances create jenkins-master jenkins-slave  --zone=us-central1-b \
    --machine-type=e2-medium \
    --create-disk=auto-delete=yes,boot=yes,image=projects/ubuntu-os-cloud/global/images/ubuntu-2004-focal-v20241115,mode=rw,size=10,type=pd-balanced

gcloud compute instances create ansible-controller --zone=us-central1-b \
    --machine-type=e2-medium \
    --create-disk=auto-delete=yes,boot=yes,image=projects/ubuntu-os-cloud/global/images/ubuntu-2004-focal-v20241115,mode=rw,size=10,type=pd-balanced
Go to henkins-master ssh comamnd copy that and same for slave as well  In cloud shell you do pluus paste this command then after another plus tab second command
gcloud compute ssh --zone "us-central1-b" "jenkins-master" --project "proj-k-481112"
gcloud compute ssh --zone "us-central1-b" "jenkins-slave" --project "proj-k-481112"

In cloud sheell rrun ansible controller gclud command then after
sudo -i
adduser ansible
vi /etc/ssh/sshd_config  iin this comment include and uncomment password authentication yes
service sshd restart
visudo
  ansible ALL=(ALL)       NOPASSWD: ALL  add this ctrl x then y enter
# Restart the sshd service
service sshd restart
# Install ansible only on the controller 
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
