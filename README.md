# k8s-vm
1. Download ubuntu-20.04-server-cloudimg-amd64.img image from Ubuntu Cloud Image Site
2. Run build.sh (change docker repo to your repo)
3. Create namespace using command kubectl create ns s-sungam
4. Create VM image using command kubectl apply -f ubuntu-cloud-base-datavolume.yaml (change url to your docker repo as the same as step 2)
5. Verify PVC to come up and bound using command kubectl get pvc -n s-sungam
6. Create VM using command kubectl apply -f vm_ubuntu.yml
7. Verify VM is ready and in shutdown state using command kubectl get vm -n s-sungam
8. Start VM instance using command virtctl start vm1 -n s-sungam
9. Access to VM instance via console using command virtctl console vm1 -n s-sungam
10. Expose VM instance ssh port using command virtctl expose vmi vm1 --name=vm1-ssh --port=20222 --target-port=22 --type=NodePort -n s-sungam
11. You should be able to ssh to the VM instance using ubuntu@[k8s node ip]:20222 with password ubuntu
