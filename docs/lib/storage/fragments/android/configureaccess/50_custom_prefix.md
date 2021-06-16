// TODO: below code snippets need to be verified

<amplify-block-switcher>
<amplify-block name="Java">

```java
// TODO: this is swift
struct CustomOverrideKeyResolver: AWSS3PluginCustomKeyResolver {
    func resolvePrefix(for accessLevel: StorageAccessLevel,
                        targetIdentityId: String?) -> Result<String, StorageError> {
        switch accessLevel {
        case .guest:
            return .success("myPublicPrefix/")
        case .protected:
            return .failure(.configuration("`.protected` StorageAccessLevel is not used", "", nil))
        case .private:
            return .failure(.configuration("`.protected` StorageAccessLevel is not used", "", nil))
        }
    }
}
```

Use it in the request options
```java
AWSS3PluginOptions pluginOptions = AWSS3PluginOptions.builder()
    .customKeyResolver((accessLevel, targetIdentityId) -> {
       // TODO - define this above
    }
    .build()
 StorageUploadFileOptions options = StorageUploadFileOptions.builder()
    .pluginOptions(pluginOptions)
    .build()
    
Amplify.Storage.uploadFile(
        "ExampleKey",
        exampleFile,
        options,
        result -> Log.i("MyAmplifyApp", "Successfully uploaded: " + result.getKey()),
        storageFailure -> Log.e("MyAmplifyApp", "Upload failed", storageFailure)
);
```

If you would like to define no prefix resolution logic, such as perform S3 requests at the root of the bucket, use `AWSS3PluginOptions.passThroughKeyResolver`.

```java
// TODO: verify this
AWSS3PluginOptions pluginOptions = AWSS3PluginOptions.passThroughKeyResolver
```

</amplify-block>
<amplify-block name="Kotlin - Callbacks">

```kotlin
// TODO: this is swift
struct CustomOverrideKeyResolver: AWSS3PluginCustomKeyResolver {
    func resolvePrefix(for accessLevel: StorageAccessLevel,
                        targetIdentityId: String?) -> Result<String, StorageError> {
        switch accessLevel {
        case .guest:
            return .success("myPublicPrefix/")
        case .protected:
            return .failure(.configuration("`.protected` StorageAccessLevel is not used", "", nil))
        case .private:
            return .failure(.configuration("`.protected` StorageAccessLevel is not used", "", nil))
        }
    }
}
```

Use it in the request options
```kotlin
val pluginOptions = AWSS3PluginOptions.builder()
    .customKeyResolver((accessLevel, targetIdentityId) -> {
       // TODO - define this above
    }
    .build()
val options = StorageUploadFileOptions.builder()
    .pluginOptions(pluginOptions)
    .build()
    
Amplify.Storage.uploadFile(
    "ExampleKey", 
    exampleFile,
    options, { Log.i("MyAmplifyApp", "Successfully uploaded: ${it.key}") },{ Log.e("MyAmplifyApp", "Upload failed", it) })
```

If you would like to define no prefix resolution logic, such as perform S3 requests at the root of the bucket, use `AWSS3PluginOptions.passThroughKeyResolver`.

```kotlin
// TODO: verify this
AWSS3PluginOptions pluginOptions = AWSS3PluginOptions.passThroughKeyResolver
```

</amplify-block>
<amplify-block name="Kotlin - Coroutines (Beta)">

```kotlin
// TODO: ths is swift
struct CustomOverrideKeyResolver: AWSS3PluginCustomKeyResolver {
    func resolvePrefix(for accessLevel: StorageAccessLevel,
                        targetIdentityId: String?) -> Result<String, StorageError> {
        switch accessLevel {
        case .guest:
            return .success("myPublicPrefix/")
        case .protected:
            return .failure(.configuration("`.protected` StorageAccessLevel is not used", "", nil))
        case .private:
            return .failure(.configuration("`.protected` StorageAccessLevel is not used", "", nil))
        }
    }
}
```

Use it in the request options
```kotlin
val pluginOptions = AWSS3PluginOptions.builder()
    .customKeyResolver((accessLevel, targetIdentityId) -> {
       // TODO - define this above
    }
    .build()
val options = StorageUploadFileOptions.builder()
    .pluginOptions(pluginOptions)
    .build()
val upload = Amplify.Storage.uploadFile("ExampleKey", exampleFile, options)
```

If you would like to define no prefix resolution logic, such as perform S3 requests at the root of the bucket, use `AWSS3PluginOptions.passThroughKeyResolver`.

```kotlin
// TODO: verify this
AWSS3PluginOptions pluginOptions = AWSS3PluginOptions.passThroughKeyResolver
```

</amplify-block>
</amplify-block-switcher>
