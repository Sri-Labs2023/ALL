# Tekton
~~~
Tekton Pipelines is an open-source project that focuses on providing a Kubernetes-native, lightweight,
easy-to-manage serverless CI/CD framework. Tekton is built for Kubernetes and runs delivery pipelines in pods
to scale on demand, and allow teams to fully control their pipelines and dependencies.
~~~

![u888](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/9dd0212e-15e4-489c-a42a-d74847fe3f2c)
![7680](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/c3947737-1d7f-4892-9f60-8eaa7073a952)
![476](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/80d90a82-3066-4ba6-99b8-c4fd5acbfe2a)
![5447](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/dc1db235-3efa-4f3b-a088-c35c29e342ca)
![6577](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/718ffafd-035f-4d82-a1a5-29a8778ec8ab)
![364646](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/e1bbcb84-2732-42c0-b87e-923c335689bd)
![56757](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/86211090-fdff-476a-abfe-eca8b6f66afc)

![Screenshot 2023-09-12 163058](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/1bda79ba-55c2-4d90-879b-a3573b89f916)
![Screenshot 2023-09-12 154015](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/932b4020-2fe7-4817-9c14-0d5522a7dbeb)
![Screenshot 2023-09-12 162906](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/a6710d8d-8402-4fc7-a32f-6825f565afd4)
![Screenshot 2023-09-12 165407](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/ae0c23b8-6a79-44c5-a484-5a239edc8487)
![Screenshot 2023-09-12 165657](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/6ec1cf29-9f16-418c-8151-70321f8b82cf)
![5757](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/7525d10e-bc48-468e-8809-d8b48bb3a275)
![79879](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/9fb43195-e307-42c1-8624-d41a2f74f886)
![9798](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/718741bf-41ac-45e9-8eb9-d430c0cc65e5)
![7](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/f3dcbd72-aeb8-470c-aabf-e1f92e8c9fc2)
![768](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/715f4891-84f3-45c0-a154-130ceec1d08b)
![78](https://github.com/Sri-Labs2023/Zfn-ALL/assets/141903669/f9ab4121-5817-46b2-9480-c38652aaf308)


# Tekton Dashboard Installation

~~~
kubectl create namespace tekton-pipelines
kubectl apply -f https://storage.googleapis.com/tekton-releases/dashboard/previous/v0.39.0/release.yaml
kubectl port-forward -n tekton-pipelines service/tekton-dashboard 8484:9097
~~~

# Tekton Pipeline and Webhook Setup

~~~
kubectl apply -f https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml
~~~
