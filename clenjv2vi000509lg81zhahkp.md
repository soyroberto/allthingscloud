---
title: "Upload a Windows 10 VM to Azure Resource Manager"
datePublished: Tue Feb 28 2023 01:08:03 GMT+0000 (Coordinated Universal Time)
cuid: clenjv2vi000509lg81zhahkp
slug: upload-a-windows-10-vm-to-azure-resource-manager
tags: azure, windows, windows-server

---

I needed to upload and create a Windows 10 image to an Azure tenant that didn't have one available. Most of them don't unless they're given as part of an MSDN subscription. This is the **How-To**.

The steps:

1. Create a base image with the features, software, patches and whatever else you need
    
2. Mark it as image
    
3. Upload it to Azure - ARM mode
    
4. Create the image from the base
    

Here's the original desktop I created on my Azure tenant :

\[caption id="" align="aligncenter" width="2556"\]

![](https://xv3aiw.bn1304.livefilestore.com/y4mM2uorroltHneJuNWrBBnSN7Ers9blUAB5PDBzxZjCn-ch3HenWyWkVnYJMI-Z5vc0DEG34x2IVX3wA4PeFI2b8lsy3qbgL-V1YmWkErLk4wDyii-12NAokuvHF6-vBO0D7-nVmuhBdbDXlxHT59h3Ff9H_NXTUPQjwgVCuMHjWD5P32JUPYckNpn4zFyZm-hLKD7k_AaS2RJdkp6YRxPLg?width=2556&height=1320&cropmode=none align="left")

Hello Windows 10, Windows 10 N actually. Same Windows but with no Media Related Technologies\[/caption\]

\[caption id="" align="aligncenter" width="1730"\]

![](https://ic0sgq.bn1304.livefilestore.com/y4mYWsWMznVtmbSxptC8Tp8NwissyfrlIHN5wqK2JPk4EUvrdYoMKZ8NVYfxgtufHVrqQs0kwgeZHXy3bS5ULbt-PADaIEKesc4TjiYTK_eLHMv1-V-BfWU7PwPzloqbXsLBEgQJvIqvQ-gCbudWW9dsaw70NjGNi6MSd-Bpfk3Fk8EFXSAMO6VI3VoS2HFCDTe6F1gxwJQWsh168hSlbYpMA?width=1730&height=428&cropmode=none align="left")

I properly called it Windows10Base\[/caption\]

\[caption id="" align="aligncenter" width="2130"\]

![](https://w4gy6q.bn1304.livefilestore.com/y4ma8eXXWqbb9JKY0danCkfRVbZa-oM54BYfZ7XschUmavfCSMnNc5NB_iMKzhz1iwCXI5xvZqI7Asuvc15wrHhY8g4iPyoL7qVwJKNvN_lbFxbCKy15MbGjFATmp2b3aAia8LfFBetyLoJfP-hl2PZYRewRJ3F2clhqKbgk7FKenJe6vqTRyuA5HBgi6hl2AE7zwjX1D37SXzOMeufAW1OZQ?width=2130&height=1310&cropmode=none align="left")

After patching and adding all the required components. The next step is to run *sysprep*\[/caption\]

\[caption id="" align="aligncenter" width="582"\]

![](https://xv2qiw.bn1304.livefilestore.com/y4mFqZSiHnIZt85vPMtzk6jqiNDnnhRIBfXd8CNDWcJ1bxyQYmOi7tvvDGbkmJfuQwdBr-2LOZK2mNriRSgX2LLvbECiXIOixgZTTnSwmTSLEpCZyUkl986YMoxu6nYWfn1_umN4lZHLZegU0XejhyYUKdRFE1LTMJoyXSGbYKGEtBnYq9e-oJxapcXA7zMV4yZXnThg5oqhshDjXfPeOaSLg?width=582&height=348&cropmode=none align="left")

It normally takes 10 to 15 minutes to finish. Once it's done, the VM will be deleted form the Tenant, the VM, not the disk.\[/caption\]

\[caption id="" align="alignnone" width="1822"\]

![](https://kbrwrg.bn1304.livefilestore.com/y4msYJ_TadX2BC3_cD-FajYMudti6friRzTDJjCJFZf4nRVTgsb2klE764GanUO3P6FbVTZRBgXthdTk9JuW1uRAShJVYWx1QeLDSCtNrKRsW84ysA-jGwUyO5kIlUWHdJ5oHbqGy4PW2nKrbPw9tBUsJBIDQoj3dKtA47C3MwoJSMAUUEwhhZGLtCyFysn2lWV0cjItccCZOob2eC2i-dJkA?width=1822&height=662&cropmode=none align="left")

Here's the sysprep-ed VHD to be used as an image\[/caption\]

**Note**: You have to shutdown the VM and mark it as image after the ***sysprep*,** if this is not done, the VM will not be able to be used as an image to create other VMs

```plaintext
Stop-AzureRmVM -ResourceGroupName '<Your Resource Group here>' -Name '<Vm Name>'
Set-AzureRmVM -ResourceGroupName '<Your Resource Group Name' -Name ''<VM Name>"  -Generalized
```

Next, was to download the .***vHD***. Remember this was created in one subscription and uploaded to another.

\[caption id="" align="aligncenter" width="2638"\]

![](https://8iohaq.bn1304.livefilestore.com/y4mHdR0M17pYCp2KdEr9ab-S9UCu22ufMuvX8cYCV_VnnMp5e0ZH5Yppnrltl2xIsxDJOH5h5hdM8oPwXa88kCmIN40t9t8PQdwdpYDP_r1nmzcEXUBSPTValbxpX7BLfQc373ypyI2LqgvkMyfTfp1c6VB-hrgQAVE68CNk8P8qVxu6ZRpYjpm70_ESP8inKzg30TQDeefijfvg_lxUoJogA?width=2638&height=590&cropmode=none align="left")

I used the Azure Storage Explorer in a Windows Box\[/caption\]

Now I had the .***vHD*** file locally, it can be uploaded to the corresponding storage account in the target subscription.

The quick steps:

```plaintext
Login-AzureRmAccount - It will challenge you to provide the username/password set
```

```plaintext
Select-AzureRmSubscription -SubscriptionId "xxxx-xxxx-xxxx-xxxx" - In case you have access to more than one subscription

```

I created a container inside a storage account for this .***vHD*** https://\[whatevernamesuitsyou\].[blob.core.windows.net/vhd](http://blob.core.windows.net/vhd)

Time to upload the .**vHD** to the target Subscription

```plaintext
Add-AzureRmVhd -ResourceGroupName [YourResourceGroupName] `
-Destination "https://[whatevernamesuitsyou].blob.core.windows.net/vhd/windows10basehd.vhd" `
-LocalFilePath .\Windows10Base2016326141340.vhd
```

It will look like this:

\[caption id="" align="aligncenter" width="2550"\]

![](https://togt6q.bn1304.livefilestore.com/y4mYi7ea5dNz2KJ79YgcUzDjYzAnQkrKUYg3XTldUztftoLlORvmL0u7Q6-3VsxktZGITwLMFD-Up7GxQNxgXDkqzKvQ4jfo-wPHgAQM0JiwPm42ZY-TOYbwSpLWETNiJHQ-YDyn0VI_RZB8PRDx-aDKVhq8f3sUy7Hmr3WSIxyNi6rhohFdHE89BSvFHu4VLty-_cGyDX37buO63MofzqePw?width=2550&height=596&cropmode=none align="left")

It took 1 1/2 hours to upload\[/caption\]

The .***vHD*** is up, now what?

## Time to create the Virtual Machine

```plaintext
#By Roberto Lopez aka @soyroberto
#modified from
#https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-upload-image
#April 2016
# You can copy/paste this code and adjust it, as long as your VHD is up and generalised
#You have to fill all things in ""
$rgname = ""  #change it to your corresponding RG name
$storageAccName = "" #change it to your storage account name
$location = "" # put your Azure region here
$vnet = "" #adjust your Vnet Name here

#change names below for uniqueness
As an improve you could modify the variables below to make them automatic.
$nicname = "" #name of the Card for the VM
$vmname = "" #Name of VM. This is the name you see in the Azure portal
$computerName = "" #Computer name of the VM/The one you see in Windows
$osDiskName = "" #Name of the HDD
$pipname ="" #IP - Name of the IPcard
$urlOfUploadedImageVhd = "" # The base Image VHD uploaded, syspreped and marked as an OS
 
#changes finished , sort of
$pip = New-AzureRmPublicIpAddress -Name $pipname -ResourceGroupName $rgname -Location $location -AllocationMethod Dynamic
$vnetname = Get-AzureRmVirtualNetwork -Name $vnet -ResourceGroupName $rgname
$subnetid = (Get-AzureRmVirtualNetworkSubnetConfig -Name 'default' -VirtualNetwork $vnetname).id #the name of the Vnet the VM will be created
#changes finished
$nic = New-AzureRmNetworkInterface -Name $nicname -ResourceGroupName $rgName -Location $location -PublicIpAddressId $pip.Id -SubnetId $subnetid # -subnetid $vnet.Subnets[0].Id
#Get the storage account where the uploaded image is stored
$storageAcc = Get-AzureRmStorageAccount -ResourceGroupName $rgName -AccountName $storageAccName
#Set the VM name and size
#Use "Get-Help New-AzureRmVMConfig" to know the available options for -VMsize
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize "Standard_DS2_v2"
#Set the Windows operating system configuration and add the NIC
orig $vm = Set-AzureRmVMOperatingSystem -VM $vmConfig -Windows -ComputerName $computerName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm = Set-AzureRmVMOperatingSystem -VM $vmConfig -Windows -ComputerName $computerName  -ProvisionVMAgent -EnableAutoUpdate
$vm = Add-AzureRmVMNetworkInterface -VM $vm -Id $nic.Id
#Create the OS disk URI
$osDiskUri = '{0}vhds/{1}{2}.vhd' -f $storageAcc.PrimaryEndpoints.Blob.ToString(), $vmName.ToLower(), $osDiskName
#Configure the OS disk to be created from image (-CreateOption fromImage) and give the URL of the uploaded image VHD for the -SourceImageUri parameter
#You can find this URL in the result of the Add-AzureRmVhd cmdlet above
$vm = Set-AzureRmVMOSDisk -VM $vm -Name $osDiskName -VhdUri $osDiskUri -CreateOption fromImage -SourceImageUri $urlOfUploadedImageVhd -Windows
#Create the new VM
New-AzureRmVM -ResourceGroupName $rgName -Location $location -VM $vm
End of Script
```

And that's it

You will have a  Windows 10 VM created in Azure ARM

[@soyroberto](http://twitter.com/soyroberto)