```swift
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
```swift
let pluginOptions = AWSS3PluginOptions(customKeyResolver: CustomOverrideKeyResolver())        
let uploadOptions = StorageUploadDataRequest.Options(pluginOptions: pluginOptions)
Amplify.Storage.uploadData(key: key, data: data, options: uploadOptions) 
```

If you would like to define no prefix resolution logic, such as perform S3 requests at the root of the bucket, use `AWSS3PluginOptions.passThroughKeyResolver`.

```swift
let uploadOptions = StorageUploadDataRequest.Options(pluginOptions: AWSS3PluginOptions.passThroughKeyResolver)
Amplify.Storage.uploadData(key: key, data: data, options: uploadOptions) 
```