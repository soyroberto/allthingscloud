---
title: "Enforcing Azure Tag Compliance with Azure Policy: A Step-by-Step Guide to Automating Tagging"
seoTitle: "Automate Azure Tagging with Policy Compliance"
seoDescription: "Learn how to enforce Azure tag compliance with Azure Policy by automating tagging on resources. Step-by-step code breakdown included"
datePublished: Wed Feb 19 2025 04:53:50 GMT+0000 (Coordinated Universal Time)
cuid: cm7bfugyx00010al5cpug8zp7
slug: enforcing-azure-tag-compliance-with-azure-policy-a-step-by-step-guide-to-automating-costcenter-tagging
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/CqKNkmNNLnI/upload/7776c3eb6ca54d07b81c4f655cbcc067.jpeg
tags: azure, azure-devops

---

Let’s break down the provided Azure Policy code shown below line by line. This policy is designed to enforce a specific tag (`CostCenter`) on resources by modifying them if the tag is missing. Here’s the detailed explanation:

### **Code Breakdown**

```json
"policyRule": {
    "if": {
        "field": "tags['CostCenter']",
        "exists": "false"
    },
    "then": {
        "effect": "modify",
        "details": {
            "roleDefinitionIds": [
                "/providers/microsoft.authorization/roleDefinitions/b24988ac-6180-42a0-ab88-20f7382dd24c"
            ],
            "operations": [{
                "operation": "addOrReplace",
                "field": "tags['CostCenter']",
                "value": "[resourcegroup().tags['CostCenter']]"
            }]
        }
    }
}
```

---

### **1\.** `policyRule` Section

This is the main section that defines the logic of the policy. It consists of two parts: `if` (the condition) and `then` (the action to take if the condition is met).

---

### **2\.** `if` Condition

```json
"if": {
    "field": "tags['CostCenter']",
    "exists": "false"
}
```

* **Purpose**: This defines the condition that the policy evaluates.
    
* `field`: `tags['CostCenter']`:
    
    * This checks the `CostCenter` tag on the resource.
        
    * The `field` keyword is used to specify the property of the resource to evaluate.
        
* `exists`: `false`:
    
    * This checks whether the `CostCenter` tag **does not exist** on the resource.
        
    * **If the tag is missing, the condition evaluates to** `true`**, and the policy will take action.**
        

---

### **3\.** `then` Action

```json
"then": {
    "effect": "modify",
    "details": {
        "roleDefinitionIds": [
            "/providers/microsoft.authorization/roleDefinitions/b24988ac-6180-42a0-ab88-20f7382dd24c"
        ],
        "operations": [{
            "operation": "addOrReplace",
            "field": "tags['CostCenter']",
            "value": "[resourcegroup().tags['CostCenter']]"
        }]
    }
}
```

* **Purpose**: This defines the action to take if the `if` condition is true (i.e., the `CostCenter` tag is missing).
    

#### `effect`: `modify`

* The `modify` effect is used to **change the resource** to bring it into compliance.
    
* In this case, it will add or replace the `CostCenter` tag on the resource.
    

#### `details` Section

This section specifies how the `modify` effect will be applied.

##### `roleDefinitionIds`

```json
"roleDefinitionIds": [
    "/providers/microsoft.authorization/roleDefinitions/b24988ac-6180-42a0-ab88-20f7382dd24c"
]
```

* **Purpose**: Specifies the role required to perform the `modify` operation.
    
* **Role ID**: `b24988ac-6180-42a0-ab88-20f7382dd24c` corresponds to the **Contributor** role in Azure.
    
    * The Contributor role has the necessary permissions to modify resources, including adding or replacing tags.
        

##### `operations`

```json
"operations": [{
    "operation": "addOrReplace",
    "field": "tags['CostCenter']",
    "value": "[resourcegroup().tags['CostCenter']]"
}]
```

* **Purpose**: Defines the specific operation to perform on the resource.
    
* `operation`: `addOrReplace`:
    
    * This operation will **add the tag if it doesn’t exist** or **replace its value if it already exists**.
        
* `field`: `tags['CostCenter']`:
    
    * Specifies the target field to modify, which is the `CostCenter` tag.
        
* `value`: `[resourcegroup().tags['CostCenter']]`:
    
    * This is a **policy function** that retrieves the value of the `CostCenter` tag from the **resource group** that the resource belongs to.
        
    * The tag value is inherited from the resource group and applied to the resource.
        

---

### **How This Policy Works**

1. **Evaluation**:
    
    * The policy evaluates whether the `CostCenter` tag exists on a resource.
        
    * If the tag is missing, the condition (`if`) evaluates to `true`.
        
2. **Action**:
    
    * The policy applies the `modify` effect.
        
    * It uses the **Contributor** role to add or replace the `CostCenter` tag on the resource.
        
    * The value of the `CostCenter` tag is inherited from the resource group.
        
3. **Result**:
    
    * If the `CostCenter` tag is missing, it will be added to the resource with the value from the resource group.
        
    * If the `CostCenter` tag already exists but has a different value, it will be replaced with the value from the resource group.
        

---

### **Example Scenario**

* **Resource Group**:
    
    * Has a `CostCenter` tag with the value `Finance`.
        
* **Resource**:
    
    * Does not have a `CostCenter` tag.
        
* **Policy Action**:
    
    * The policy adds the `CostCenter` tag to the resource with the value `Finance` (inherited from the resource group).
        

---

### **Key Points**

* **Tag Inheritance**: This policy ensures that resources inherit the `CostCenter` tag from their resource group, promoting consistency.
    
* **Compliance**: The `modify` effect automatically brings non-compliant resources into compliance by adding or updating the tag.
    
* **Role-Based Access**: The policy requires the Contributor role to perform the modification, ensuring proper permissions are in place.
    

---

Roberto w/assistance from DeepSeek