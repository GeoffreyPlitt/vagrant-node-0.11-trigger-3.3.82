Vagrant.configure("2") do |config|
  config.vm.box = "vagrant-node-0.10-0.0.1"
  config.vm.box_url = "https://github.com/GeoffreyPlitt/vagrant-node-0.11/releases/download/0.0.1/vagrant-node-0.11-0.0.1.box"
  config.vm.provision :shell, :inline => $BOOTSTRAP_SCRIPT # see below
end

$BOOTSTRAP_SCRIPT = <<EOF
  set -e # Stop on any error

  export DEBIAN_FRONTEND=noninteractive

  # Trigger toolkit.
  if [ ! -e /usr/bin/TriggerToolkit/ ]; then
    wget https://toolkit-installer.s3.amazonaws.com/3.3.82/TriggerToolkit.tar.gz
    tar zxvf TriggerToolkit.tar.gz
    sudo mv TriggerToolkit /usr/bin/
    echo 'PATH=/usr/bin/TriggerToolkit/:$PATH' | sudo tee -a ~vagrant/.profile
  fi

  echo VAGRANT IS READY.
EOF
