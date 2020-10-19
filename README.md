# gcp-org-policy-organization-appengine

## Boolean options:
1. Inherited
(Project from Folder and Organization)
(Folder from Organization)
2. Enabled
3. Disabled

### Examples:

#### Boolean Enabled

```yaml
constraint: constraints/compute.requireOsLogin
booleanPolicy:
  enforced: true
```

#### Boolean Disabled

```yaml
constraint: constraints/compute.requireOsLogin
booleanPolicy:
  enforced: false
```

#### To set a Boolean Constraint to "Inherited" inheritance type

```bash
gcloud resource-manager org-policies delete cloudfunctions.allowedIngressSettings --organization <project-id>
```

## List options: 
1. Inherited
(Project from Folder and Organization)
(Folder from Organization)
2. Google-managed default 
(Allow - All)
3. Custom 
(Enforce an All List)
(Enforce a Deny List) 


### Examples:

#### To set a List Constraint set to "Google-managed default" inheritance type

```yaml
constraint: constraints/iam.allowServiceAccountCredentialLifetimeExtension
restoreDefault: {}
```

#### List type - Enforce Disallow list

```yaml
constraint: constraints/iam.allowServiceAccountCredentialLifetimeExtension
listPolicy:
  deniedValues:
  - Test
  inheritFromParent: true
```

#### To Merge with Parent (Rules are combined at all levels regardless of hierarchy. "Deny" overrides "allow".) use 'inheritFromParent: true' in the yaml. To Ignore the parent's policy and use these rules do not use 'inheritFromParent: true' in the yaml.

#### List type - Enforce Allow list

```yaml
constraint: constraints/compute.restrictVpnPeerIPs
listPolicy:
  allowedValues:
  - All
```

#### To set a Boolean Constraint to "Inherited" inheritance type
```bash
gcloud resource-manager org-policies delete cloudfunctions.allowedIngressSettings --organization <project-id>
```
