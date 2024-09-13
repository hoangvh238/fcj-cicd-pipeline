---
title : "Setup Sonar plugin ( optional)"
date :  "`r Sys.Date()`" 
weight : 18
chapter : false
pre : " <b> 5.1.2.2. </b> "
---
### Step 1. Install plugins

- Access *Dashboard/Manage Jenkin/Plugins* and install **SonarQube Scanner.**

![2.png](210e856d-5b0f-4fd7-aa39-aa8c891958d8.png)

### Step 2. Config plugins

- .NET projects must use MSBuild. If you're not using .NET, you can configure the plugin as shown below:

![3.png](70489a43-09ee-49a1-a854-f8931a16975f.png)

- Nodejs or anything

![image.png](image.png)

### Step 3. Create new SonarQube credentails

- Access *Dashboard/Manage Jenkin/Credentials a*nd create new *Credentials*  **.**

![5.png](f3e638e2-a76d-4d2c-b26f-9457b103dbf6.png)

- In the "**Secret**" field, paste the key you last created in the SonarQube dashboard.

![6.png](51f22949-95ea-4a20-94de-fef3029ce692.png)

### Step 4. Config global variance for plugins

![7.png](3078cd74-802f-4ceb-9efa-0c5868ce908b.png)