# data formats

## json format
``` javascript
devops = {
  "skill":"DevOps",
  "Year":2025,
  "Tech": {
    "Cloud":"AWS",
    "Containers":"Kubernetes",
    "CI/CD":"Jenkins",
    "GitOps": [
  	  "Gitlab",
  	  "ArgoCD",
  	  "Tekton"
  	]
  }
}
```

## yaml format
``` yaml
devops:
  skill: "DevOps"
  Year: 2023
  Tech:
    Cloud: AWS
    Containers: Kubernetes
    "CICD": Jenkins
    GitOps:
      - Gitlab
      - ArgoCD
      - Tekton
```

