// TODO: below code snippets need to be verified
```dart
// TODO: THIS IS SWIFT
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
```dart
AWSS3PluginOptions pluginOptions = AWSS3PluginOptions(customKeyResolver: CustomOverrideKeyResolver());
S3UploadFileOptions options = S3UploadFileOptions(
    pluginOptions: pluginOptions);

try {
  UploadFileResult result = await Amplify.Storage.uploadFile(
    key: key,
    local: local,
    options: options
  );
} on StorageException catch (e) {
  print(e.message);
}
```

If you would like to define no prefix resolution logic, such as perform S3 requests at the root of the bucket, use `AWSS3PluginOptions.passThroughKeyResolver`.

```dart
AWSS3PluginOptions pluginOptions = AWSS3PluginOptions(customKeyResolver: AWSS3PluginOptions.passThroughKeyResolver);
S3UploadFileOptions options = S3UploadFileOptions(
    pluginOptions: pluginOptions);

try {
  UploadFileResult result = await Amplify.Storage.uploadFile(
    key: key,
    local: local,
    options: options
  );
} on StorageException catch (e) {
  print(e.message);
}
```