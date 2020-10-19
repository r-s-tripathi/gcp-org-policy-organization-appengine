# gcp-org-policy-organization-appengine


####Boolean Options:
1. Inherited (Project to Folder and Org; or Folder to Org)
2. Enabled
3. Disabled

###Examples:

##Boolean Enabled

constraint: constraints/compute.requireOsLogin
booleanPolicy:
  enforced: true

##Boolean Disabled

constraint: constraints/compute.requireOsLogin
booleanPolicy:
  enforced: false

##To set a Boolean Constraint to "Inherited" inheritance type
#gcloud resource-manager org-policies delete cloudfunctions.allowedIngressSettings --organization <project-id>


####List Options: 
1. Inherited
2. Google-managed default (Allow - All)
3. Custom (Enforce an All List, or 4. Enforce a Deny List) 

To Ignore the parent's policy and use these rules.
To Merge with Parent (Rules are combined at all levels regardless of hierarchy. "Deny" overrides "allow".) use 'inheritFromParent: true' in the yaml. To Ignore the parent's policy and use these rules do not use 'inheritFromParent: true' in the yaml.

###Examples:

##To set a List Constraint set to "Google-managed default" inheritance type

constraint: constraints/iam.allowServiceAccountCredentialLifetimeExtension
restoreDefault: {}

##List type - Enforce Disallow list

constraint: constraints/iam.allowServiceAccountCredentialLifetimeExtension
listPolicy:
  deniedValues:
  - Test
  inheritFromParent: true
  
##List type - Enforce Allow list

constraint: constraints/compute.restrictVpnPeerIPs
listPolicy:
  allowedValues:
  - All
  
##To set a Boolean Constraint to "Inherited" inheritance type
gcloud resource-manager org-policies delete cloudfunctions.allowedIngressSettings --organization <project-id>
  
