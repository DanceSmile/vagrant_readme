### vagrant 虚拟机管理

@(vagrant 虚拟机管理)


vrgrant 官网地址  https://www.vagrantup.com/

##### 添加box

box 官方仓库 https://app.vagrantup.com/boxes/search

	查看本机有没有可用的box （查看box列表）
	vagrant box list
	输出
	There are no installed boxes! Use `vagrant box add` to add some.
	
	直接添加box到本地
	vagrant  box add laravel/homestead
	
	
#### 初始化 启动 链接

	初始化box 
	mkdir cailei 
	cd calei 
	vagrant init  laravel/homestead
	启动box
	vagrant up
	链接box
	vagrant  ssh
	
> 初始化 **box** 会到当前的文件夹生成一个 **Vagrantfile** ，初始化 **box** 会将镜像导入到虚拟机。并且在虚拟机的根目录建立一个 Vagrant的文件夹和本地当前的文件夹 作为共享文件夹

#### 状态查看  启动  关机  重启  销毁  暂停 恢复

	查看虚拟机状态
	进入目录 执行
	vagrant status
	输出
	Current machine states:
	
	default                   running (virtualbox)
	
	The VM is running. To stop this VM, you can run `vagrant halt` to
	shut it down forcefully, or you can run `vagrant suspend` to simply
	suspend the virtual machine. In either case, to restart it again,
	simply run `vagrant up`.

---

	虚拟机关机
	vagrant halt

---

	启动虚拟机
	vagrant up

---

	暂停虚拟机
	vagrant suspend
	恢复虚拟机
	vagrant resume

---

	 重启虚拟机
	 vagrant reload

---

	销毁虚拟机
    vagrant destroy


#### 添加额外的共享目录

	  config.vm.synced_folder "./data", "/vagrant_data",
	  create:true,
	  owner:"root",
	  group:"root"

#### 网络配置

	 私有网络配置
	 config.vm.network "private_network", ip: "192.168.33.10"

---

	 公有网络
	 config.vm.network "public_network"
	 
---

	端口转发
	config.vm.network "forwarded_port", guest: 80, host: 8080
 

####  文件权限

	  config.vm.synced_folder "./www", "/vagrant_data",
	  owner:'nginx',
	  group:'nginx',
	  create:true,
	  mount_options:["dmode=777","fmode=777"]
 
