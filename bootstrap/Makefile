

/etc/k3s-resolv.conf:
	echo "nameserver 10.1.0.1" | sudo tee /etc/k3s-resolv.conf


create: /etc/k3s-resolv.conf
	k3d cluster create -c ./configs/k3d.core.yaml
	kubectl create namespace flux-system
	kubectl create secret generic --namespace flux-system flux-system -o yaml --from-file=age.agekey=../secrets/age-key.txt
	kubectl apply -k ../kubernetes/clusters/core/flux-system
	kubectl apply -f ../kubernetes/clusters/core/gitrepository.flux-system.yaml
	kubectl apply -f ../kubernetes/clusters/core/kustomization.cluster.yaml

delete:
	k3d cluster delete core
