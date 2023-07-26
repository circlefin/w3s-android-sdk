# w3s-android-sdk

## Installation

Add the maven repository to your gradle file:

```gradle
repositories {
	...
	maven { 
		url 'https://maven.pkg.github.com/circlefin/w3s-android-sdk' 
		credentials {
			username '<GITHUB_USERNAME>'
			password '<GITHUB_PAT>' // Fine-grained personal access tokens or classic with package write permission
		}
	}
}
```
It's suggest that load settings from `local.proprties`.
```gradle
repositories {
	...
	maven { 
        Properties properties = new Properties()
        properties.load(new File(rootDir.absolutePath + "/local.properties").newDataInputStream()) // load local.properties
		url properties.getProperty('pwsdk.maven.url')
		credentials {
            username properties.getProperty('pwsdk.maven.username')
            password properties.getProperty('pwsdk.maven.password')
		}
	}
}
```
local.properties
```
...
pwsdk.maven.url=https://maven.pkg.github.com/circlefin/w3s-android-sdk
pwsdk.maven.username=<GITHUB_USERNAME>
pwsdk.maven.password=<GITHUB_PAT>

```

Add the dependency:

```gradle
dependencies {
	implementation 'circle.programmablewallet:sdk:version'
}
```