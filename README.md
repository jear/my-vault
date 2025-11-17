# my-vault
```
helm repo add hashicorp https://helm.releases.hashicorp.com

k create ns vault
helm install vault hashicorp/vault -n vault
kubectl patch svc vault -n vault -p '{"spec": {"type": "LoadBalancer"}}'


 kubectl exec -ti vault-0 -- vault operator init -n vault
Error from server (NotFound): pods "vault-0" not found
(base) ubuntu@ubuntu-MVM:~/workspace/github$ k get pods -n vault
NAME                                    READY   STATUS    RESTARTS   AGE
vault-0                                 0/1     Running   0          7m51s
vault-agent-injector-556c5dd8fb-5mvft   1/1     Running   0          7m51s
(base) ubuntu@ubuntu-MVM:~/workspace/github$ kubectl exec -ti vault-0 -n vault  -- vault operator init
Unseal Key 1: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Unseal Key 2: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Unseal Key 3: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Unseal Key 4: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Unseal Key 5: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Initial Root Token: hvs.XXXXXXXXXXXXXXXXXXXXXXXX

Vault initialized with 5 key shares and a key threshold of 3. Please securely
distribute the key shares printed above. When the Vault is re-sealed,
restarted, or stopped, you must supply at least 3 of these keys to unseal it
before it can start servicing requests.

Vault does not store the generated root key. Without at least 3 keys to
reconstruct the root key, Vault will remain permanently sealed!

It is possible to generate new unseal keys, provided you have a quorum of
existing unseal keys shares. See "vault operator rekey" for more information.
```
