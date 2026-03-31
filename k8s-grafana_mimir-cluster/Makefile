USER ?= h.abingwa
ASKPASS ?= --ask-pass

.PHONY: ping deploy destroy rebuild prep preflight

ping:
	sudo ansible all -m ping -u $(USER) $(ASKPASS) --ask-vault-pass

preflight:
	sudo ansible-playbook deploy.yml -u $(USER) $(ASKPASS) --become --ask-vault-pass --tags preflight

prep:
	sudo ansible-playbook deploy.yml -u $(USER) $(ASKPASS) --become --ask-vault-pass --tags common,containerd,kubernetes,mimir_deploy

deploy:
	sudo ansible-playbook deploy.yml -u $(USER) $(ASKPASS) --become --ask-vault-pass

destroy:
	sudo ansible-playbook destroy.yml -u $(USER) $(ASKPASS) --become --ask-vault-pass

rebuild:
	sudo ansible-playbook rebuild.yml -u $(USER) $(ASKPASS) --become --ask-vault-pass
