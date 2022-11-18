## Generating certificates from Azure Key Vault

Today I learned a way to generate certificates from Azure Key Vault.

To generate a certificate, a policy is required. You can get the default policy from your Azure subscription using the following command with the Azure CLI:

`az keyvault certificate get-default-policy | Out-File -Encoding utf8 [yourname].json ` 

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

