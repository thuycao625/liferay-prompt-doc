# Prepare environment
- add build.sdk.version=1.0.20 to build.${user.name}.properties 						
- export JAVA_OPTS="-Dhttps.protocols=TLSv1.2"						
- export ANT_OPTS="-Xmx2048m"
- export VM_ARGS = "-Xms4096m -Xmx8192m"
- java jdk: 8						

# Step to follow
- Clone git prompt
- Delete tool/sdk folder						
- cd modules
- git clean -xdf						
- cd ..						
- ant -Drepository.url=https://repository-cdn.liferay.com/nexus/content/groups/public clean						
- ant all			

# Format code
- ant setup-sdk
- cd portal-impl
- ant format-source-current-branch -Dgit.working.branch.name=78a4831fba35ab0cf3380d08443be3ec46f9f93a"					
- ant setup-sdk	

# Note
- Use "blade gw deploy" to deploy new code. Update blade if necessary				
- Use "ant deploy" to deploy portal-impl							
