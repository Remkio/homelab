

/etc/k3s-resolv.conf:
	echo "nameserver 10.1.0.1" | sudo tee /etc/k3s-resolv.conf


create: /etc/k3s-resolv.conf
	k3d cluster create -c ./configs/k3d.core.yaml
	kubectl apply -f ../kubernetes/infrastructure/base/flux-system/namespace.flux-system.yaml
	kubectl create secret generic --namespace flux-system sops-keys -o yaml --from-file=age.agekey=../secrets/age-key.txt
	kubectl apply -k ../kubernetes/infrastructure/base/flux-system
	kubectl apply -k ../kubernetes/infrastructure/core

delete:
	k3d cluster delete core
