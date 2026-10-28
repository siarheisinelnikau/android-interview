# Photo Picker vs. Storage Access Framework - when would you use each? How do scoped storage and URI permissions affect file sharing?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

The Photo Picker selects user-chosen images or videos without broad media-library access. The Storage Access Framework handles general documents and user-selected document providers, including opening, creating, or selecting a document tree through the relevant contract.

Treat the returned `content://` URI as a capability, not a filesystem path. Read through `ContentResolver`; remote providers may not expose a local path. Scoped storage limits direct access to shared storage, while URI grants authorize the selected resource.

Persist a grant only when the provider and contract support it and continued access is needed. To share an app-owned file, expose it with FileProvider and grant temporary access to the receiving app. Avoid `file://` URIs and broad permissions merely to support one selected file.

## References

- [Android: Photo Picker](https://developer.android.com/training/data-storage/shared/photopicker)
- [Android: document access](https://developer.android.com/training/data-storage/shared/documents-files)
- [Android: secure file sharing](https://developer.android.com/training/secure-file-sharing)
