# Lazy Guide
1. Download ubuntu-20.04-server-cloudimg-amd64.img image from Ubuntu Cloud Image Site
2. Run build.sh (change docker repo to your repo)
3. Create namespace using command kubectl create ns s-sungam
4. Create VM image using command kubectl apply -f ubuntu-cloud-base-datavolume.yaml (change url to your docker repo as the same as step 2)
5. Vefify VM image import is success using command kubectl get datavolume -n s-sungam
6. Verify PVC to come up and bound using command kubectl get pvc -n s-sungam
7. Create VM using command kubectl apply -f vm_ubuntu.yml
8. Verify VM is ready and in shutdown state using command kubectl get vm -n s-sungam
9. Start VM instance using command virtctl start vm1 -n s-sungam
10. Access to VM instance via console using command virtctl console vm1 -n s-sungam
11. Expose VM instance ssh port using command virtctl expose vmi vm1 --name=vm1-ssh --port=20222 --target-port=22 --type=NodePort -n s-sungam
12. You should be able to ssh to the VM instance using ubuntu@[k8s node ip]:20222 with password ubuntu
