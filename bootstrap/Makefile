
init:
	podman machine init -m 4096 --rootful --disk-size 32
	podman machine start
	podman machine ssh 'echo "nameserver 8.8.8.8" | sudo tee /etc/k3s-resolv.conf'

create:
	k3d cluster create -c ./configs/k3d.core.yaml
	kubectl create namespace flux-system
	kubectl create secret generic --namespace flux-system flux-system -o yaml --from-file=age.agekey=../secrets/age-key.txt
	kubectl apply -k ../kubernetes/clusters/core/flux-system
	kubectl apply -f ../kubernetes/clusters/core/gitrepository.flux-system.yaml
	kubectl apply -f ../kubernetes/clusters/core/kustomization.cluster.yaml

delete:
	k3d cluster delete core

destroy:
	podman machine stop
	podman machine rm -f
