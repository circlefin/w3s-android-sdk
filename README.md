# w3s-android-sdk

## Installation
Add the maven repository to your gradle file. It's suggested that load settings from `local.properties`:
```gradle
repositories {
	...
	maven { 
        	Properties properties = new Properties()
		// Load local.properties.
        	properties.load(new File(rootDir.absolutePath + "/local.properties").newDataInputStream())
			
		url properties.getProperty('pwsdk.maven.url')
		credentials {
        		username properties.getProperty('pwsdk.maven.username')
        		password properties.getProperty('pwsdk.maven.password')
		}
	}
}
```
Add the maven setting values in `local.properties` file:
```properties
pwsdk.maven.url=https://maven.pkg.github.com/circlefin/w3s-android-sdk
pwsdk.maven.username=<GITHUB_USERNAME>
# Fine-grained personal access tokens or classic with package write permission.
pwsdk.maven.password=<GITHUB_PAT> 

```

Add the dependency:

```gradle
dependencies {
	implementation 'circle.programmablewallet:sdk:version'
}
```