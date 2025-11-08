ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure("2") do |config|

    config.vbguest.auto_update = false
    config.vm.box = "ubuntu/jammy64"

    config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 2
    end


    config.vm.define "app" do |app|
        app.vm.hostname = "app"
        app.vm.network "private_network", ip: "192.168.56.10"


        app.vm.provider "virtualbox" do |vb|
            vb.name = "vagrant-app"
        end


        app.vm.synced_folder ".", "/vagrant", type: "rsync"
    end


    config.vm.define "db" do |db|
        db.vm.hostname = "db"
        db.vm.network "private_network", ip: "192.168.56.11"


        db.vm.provider "virtualbox" do |vb|
            vb.name = "vagrant-db"
        end


        db.vm.synced_folder ".", "/vagrant", type: "rsync"
    end
end
