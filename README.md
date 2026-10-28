# w3s-android-sdk

## Requirements

This SDK is built with the Kotlin 2.1 / AGP 8.7 toolchain. Consuming apps must compile with:

| Tool | Minimum version |
|---|---|
| **Kotlin compiler** | **2.1** (the SDK ships `@kotlin.Metadata(mv=[2,1,0])` and transitively depends on `kotlin-stdlib` 2.1.x — Kotlin 2.0.x compilers can only read up to `mv=[2,0,0]` and fail with `binary version of its metadata is 2.1.0, expected version is 2.0.0`) |
| **Android Gradle Plugin** | **8.0** (required to dex Kotlin 2.x runtime artifacts and to honor the SDK's compile-time toolchain metadata) |
| **JDK to run Gradle** | **17** (mandated by AGP 8 / Kotlin 2.1) |
| **Android Studio** | **Hedgehog (2023.1.1)** or newer — bundles JDK 17 by default |

The published AAR itself ships Java 8 bytecode (classfile major version 52), so the runtime / `minSdk` story is unchanged from previous releases. Only the build-time Kotlin/AGP toolchain is constrained.

## Installation
Add the maven repository to your gradle file. It's suggested that load settings from `local.properties`:
```gradle
repositories {
	...
	maven { 
        	Properties properties = new Properties()
		// Load local.properties
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