## Generating certificates from Azure Key Vault

Today I learned a way to generate certificates from Azure Key Vault.

To generate a certificate, a policy is required. You can get the default policy from your Azure subscription using the following command with the Azure CLI:

`az keyvault certificate get-default-policy | Out-File -Encoding utf8 [yourname].json ` 

**Important**: this command needs to be executed from a PowerShell prompt because Out-File is PowerShell specific.

The generated policy file will look like this:

```json
{
  "issuerParameters": {
    "certificateTransparency": null,
    "name": "Self"
  },
  "keyProperties": {
    "curve": null,
    "exportable": true,
    "keySize": 2048,
    "keyType": "RSA",
    "reuseKey": true
  },
  "lifetimeActions": [
    {
      "action": {
        "actionType": "AutoRenew"
      },
      "trigger": {
        "daysBeforeExpiry": 90
      }
    }
  ],
  "secretProperties": {
    "contentType": "application/x-pkcs12"
  },
  "x509CertificateProperties": {
    "keyUsage": [
      "cRLSign",
      "dataEncipherment",
      "digitalSignature",
      "keyEncipherment",
      "keyAgreement",
      "keyCertSign"
    ],
    "subject": "CN=CLIGetDefaultPolicy",
    "validityInMonths": 12
  }
}
```

With the above policy, you can create a certificate in your Azure Key Vault:

```powershell
 az keyvault certificate create `
 --vault-name [your-key-vault-name] `
 -n [certificate-name] `
 --policy `@[your-policy-file-name]
```

Below is a PowerShell script that can be used for creating the certificate:

```powershell
# This script will generate a certificate in Key Vault based on the default policy of Azure Key Vault. 
param (
    [string]$keyvaultName = "default-name-of-your-keyvault", 
    [string]$certificateName = "default-name-of-your-certificate"    
)

Write-Output "Getting the default policy from Key Vault"
az keyvault certificate get-default-policy | Out-File -Encoding utf8 default-policy.json

Write-Output "Creating the certificate in Key Vault"
az keyvault certificate create `
 --vault-name $keyvaultName `
 -n $certificateName `
 --policy `@default-policy.json

Write-Output "Certificate created in Key Vault"
az keyvault certificate list --vault-name $keyvaultName
```

 
