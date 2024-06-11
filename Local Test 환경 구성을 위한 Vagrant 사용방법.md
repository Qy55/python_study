# Virtualbox 및 Vagrant 구성, 설정
> 설치 링크
> Virtualbox: [Downloads – Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)
> Vagrant: [Install | Vagrant | HashiCorp Developer](https://developer.hashicorp.com/vagrant/install?product_intent=vagrant)
> Vagrant Box: [Discover Vagrant Boxes - Vagrant Cloud (vagrantup.com)](https://app.vagrantup.com/boxes/search)
- Box는 VM 이미지로 직접 받지 않아도 Vagrant를 사용해 VM을 생성 할 때 Download 수행
# Vagrantfile 작성
- 작업 Directory로 이동 후 `vagrant init ${box_name}`을 사용해 `Vagrantfile` 생성

## Box 지정
```ruby
Vagrant.configure("2") do |config|
	config.vm.box = "box_name"
end
```
- `vagrant init`명령어를 사용할 때 Box이름을 지정했다면 동일하게 Box가 지정되어 Vagrantfile 생성
- 변경하고 싶다면 `config.vm.box = `구문을 수

## CPU, Memory 설정
```ruby
config.vm.provider "virtualbox" do |vb|
	vb.cpus = 2
	vb.memory = 2048
end
```
- `do` 이후 지정한 이름으로 속성 값에 접근하는 방식
- `memory`설정은 MB 단위로 작성

## Network 설정
> Virtualbox의 Network 구성
> NAT Network: Host의 IP를 사용해 외부와 통신하는 방식의 Network. Host에서 Guest에 접근하기 위해서는 Port Forwarding 필요
> Host-Only Network: Host에 가상 Network Device를 추가해 새 IP 대역을 할당하는 Network 방식


```ruby
config.vm.network "private_network", ip: "192.168.56.3"
config.vm.network "forwarded_network", guest: 80, host: 8080, host_ip: 127.0.0.1
```
- `private_network`: Host-Only Network를 사용하는 방식
- `forwarded_network`: NAT Network를 사용하는 방식

## VM Provision 설정
```ruby
config.vm.provision "shell", inline: <<-SH
	# Something to do
SH
config.vm.provision "shell", path: "path/of/host"
config.vm.provision "file", source: "path/of/host, destination: "path/of/guest"
```
- 파일을 복사하거나, 스크립트를 수행하는 동작이 가능
- `vagrant up` 당시 수행되거나 VM이 동작중에 Vagrantfile을 수정한 경우 `vagrant provision`을 통해 별도 수행가능
	- 모든 provision 구문에 name 속성을 설정해 `vagrant provision --provision-with ${provision_name}`을 통해 특정 Provision 구문만 호출 가능

## Multi-Machine 구성
```ruby
config.vm.define "vm_name" do |vm_name|
	vm_name.vm.network "private_network", ip: "192.168.56.5"
	...
```
- 모든 구문은 동일하게 작성 가능
- define 구문안에 작성된 내용은 해당하는 VM에만 적용
- define 구문 밖의 내용은 모든 VM에 동시에 적용
- Guest 별로 다른 Resource를 할당하거나 다른 Provision을 적용하는 경우 사용

# 예시
```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "rocky/92"


  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.define "gfs1" do |gfs1|
    gfs1.vm.hostname = "gfs1.stg.vm"
    gfs1.vm.network "private_network", ip: "192.168.61.11"
  end
  config.vm.define "gfs2" do |gfs2|
    gfs2.vm.hostname = "gfs2.stg.vm"
    gfs2.vm.network "private_network", ip: "192.168.61.12"
  end
  config.vm.define "gfs3" do |gfs3|
    gfs3.vm.hostname = "gfs3.stg.vm"
    gfs3.vm.network "private_network", ip: "192.168.61.13"
  end
  config.vm.provision "shell", inline: <<-SH
    echo "# GFS HOSTS" >> /etc/hosts
    echo "192.168.61.11    gfs1.stg.vm" >> /etc/hosts  
    echo "192.168.61.12    gfs2.stg.vm" >> /etc/hosts  
    echo "192.168.61.13    gfs3.stg.vm" >> /etc/hosts  
  SH
end
```
- 3개의 Guest를 구성
- 모두 동일한 Memory와 cpu를 할당
- 각각의 Hostname 및 IP를 설정
- 모든 Guest에서 provision 수행


---
#in-workspace #vm  