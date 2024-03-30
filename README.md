# aws-s3-clone
A s3 bucket clone done in either java or golang

Idea is to use k8s to manage a couple of deployments that communicate with each other. The deployments will contain the following containers with different functions such as:
- a storage container where all the files will be held for each user.
- a container that with an application (java) where the file will be processed (maybe compressed idk yet), check the files magic bytes and it's extension type. After that it will do a short virus scan of the file.
    - When it comes to virus scans I can either implement a [java class](https://medium.com/aeturnuminc/virus-scanning-in-java-using-clamav-d60a181023df) that does that or... I could install a antivirus for that pod that performs the scan after i've checked the magic bytes and extension type. More research is needed.
- a container with the website application using HTMX with Golang. Shows that the files a user has upload do indeed appear with a link, no groupings, if it's the same file it will be replaced.
- a library in ts to communicate with the k8s cluster for uploading the image. Or it could be done purely with curl or bruno.  

## TODO
- [ ] Research how to set up the cluster with multiple deployment along with how they could communicate: 
    - [ ] Storage deployment, will this container provide the ingress location of the file?
    - [ ] File check deployment, check how to scan for viruses from the application. Java is the main language for this.
    - [ ] Tie these containers together and then try it out with CURL or Bruno.
    - [ ] Website deployment, use Golang, HTMX, Web components and tailwind. A simple webpage that shows that a user has uploaded the file along with a link to the image itself that the storage deployment provides. Nothing fancy