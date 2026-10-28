# How would you handle selected-photos access and changes to the user's selected media when targeting API 34?

[Back to questions](../../README.md#android-versions)

**Level:** Middle · **Topic:** Android Versions · **Version:** Android 14 (API 34) · **Reviewed:** 2026-10-28

## Answer

Android 14 can grant an app access to a selected subset of images and videos instead of the entire library. A custom gallery targeting API 34 must distinguish full access, partial access, and denial, and use `READ_MEDIA_VISUAL_USER_SELECTED` when managing reselection under the supported flow.

Do not cache a permanent list of accessible media based only on an earlier permission check. Refresh when the screen resumes, handle content that has become unavailable, and provide a reselection action. Compatibility behavior differs if the app has not adopted the new permission flow.

If the product only needs user-selected attachments, use the system Photo Picker instead of rebuilding a gallery and requesting broad access. Selection and permission changes are normal states, not exceptional user mistakes.

## References

- [Android 14: partial photo and video access](https://developer.android.com/about/versions/14/changes/partial-photo-video-access)
