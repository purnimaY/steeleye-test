Vagrant.configure("2") do |config|  
    config.vm.define :web do |web|
        web.vm.provider :virtualbox do |v|
            v.name = "web"
            v.customize [
                "modifyvm", :id,
                "--name", "web",
                "--memory", 512,
                "--natdnshostresolver1", "on",
                "--cpus", 1,
            ]
        end

        web.vm.box = "ubuntu/trusty64"
        web.vm.network :private_network, ip: "192.168.56.93"
        web.ssh.forward_agent = true
        web.vm.synced_folder "./", "/vagrant", :nfs => true
    end
end  
Vagrant.configure("2") do |config|
    [1,2].each do |i|
        config.vm.define "application_#{i}" do |application|
            application.vm.provider :virtualbox do |v|
                v.name = "application_#{i}"
                v.customize [
                    "modifyvm", :id,
                    "--name", "application_#{i}",
                    "--memory", 512,
                    "--natdnshostresolver1", "on",
                    "--cpus", 1,
                ]
            end

            application.vm.box = "ubuntu/trusty64"
            application.vm.network :private_network, ip: "192.168.56.9#{i}"
            application.ssh.forward_agent = true
            application.vm.synced_folder "./", "/vagrant", :nfs => true, :mount_options => ['vers=3','noatime','actimeo=2', 'tcp', 'fsc']
        end
    end
end
