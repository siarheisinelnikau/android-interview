# How do granular media permissions replace `READ_EXTERNAL_STORAGE` for apps targeting API 33? When can the Photo Picker avoid requesting broad media access?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 13 (API 33) · **Reviewed:** 2026-10-28

## Answer

On Android 13, apps targeting API 33 or later use `READ_MEDIA_IMAGES`, `READ_MEDIA_VIDEO`, or `READ_MEDIA_AUDIO` for the relevant shared media instead of relying on `READ_EXTERNAL_STORAGE`. Request only the categories required by the feature.

If the user only needs to select a few images or videos, the Photo Picker grants access to the selected items without a broad library permission. A media-management app scanning the library has different requirements from an app attaching one photo.

Check picker availability through the supported AndroidX contract and fallback behavior rather than assuming every older device has the same implementation. Open returned content URIs through `ContentResolver` and account for grant lifetime when a later background upload will consume them.

## References

- [Android 13: granular media permissions](https://developer.android.com/about/versions/13/behavior-changes-13)
- [Android: Photo Picker](https://developer.android.com/training/data-storage/shared/photopicker)
