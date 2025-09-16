#You should have run a command like:
```
openbao operator init
```
This command will output the keys and the root token, something like:
```
Unseal Keys:
  1: abcdef-12345-67890...
  2: zyxwvu-54321-09876...
  3: mnopqr-11111-22222...
  4: lkjhgf-33333-44444...
  5: asdfgh-55555-66666...

Root Token:
  s.1234567890abcdef...
```
#Step 1 – Unseal the application
##For example, if the threshold is 3 out of 5, you must provide 3 keys to unlock the system.
```
openbao operator unseal <key>
```
#Step 2 – Store the keys safely
##Once unsealed, the application stays unsealed until restarted, but you must store the keys securely for future use.
Use:
Kubernetes secrets
Vault integrations
Secure storage like AWS KMS or HashiCorp Vault

#Step 3 – Verify readiness
##After unsealing, the readiness probe should pass and the pod will be marked as Ready.
```
kubectl get pods -n <namespace>
```
##and also check the logs:
```
kubectl logs openbao-demo-0 -n <namespace>
```
