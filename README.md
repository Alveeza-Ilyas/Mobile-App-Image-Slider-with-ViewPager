# Mobile-App-Image-Slider-with-ViewPager

A simple Android app (Java) that shows a **swipeable image slider** using `ViewPager` and a custom `PagerAdapter`. Swipe left or right to move between images.

## Features

| Feature | Description |
|---------|-------------|
| **Swipeable Slider** | Swipe horizontally to browse through images |
| **Custom PagerAdapter** | `ImageAdapter` creates and removes `ImageView` pages as needed |
| **Center-Crop Images** | Images fill the whole page using `ScaleType.CENTER_CROP` |
| **Edge-to-Edge Layout** | Uses `EdgeToEdge.enable()` with window insets handling |

## Concepts Demonstrated

- Using `ViewPager` to create a horizontal paging layout.
- Extending `PagerAdapter` and overriding its core methods:
  - `getCount()` returns the number of images.
  - `isViewFromObject()` checks whether a view belongs to the object returned by the adapter.
  - `instantiateItem()` creates the `ImageView` for a page and adds it to the container.
  - `destroyItem()` removes the page when it moves out of view.
- Storing images in an `int[]` array of drawable resource IDs.
  ```java
  private int[] sliderImageId = new int[]{
      R.drawable.pic, R.drawable.wallpaper, R.drawable.wallpaper2, R.drawable.google
  };
  ```
- Attaching the adapter to the pager:
  ```java
  viewPager = findViewById(R.id.viewPage);
  imageAdapter = new ImageAdapter(this);
  viewPager.setAdapter(imageAdapter);
  ```

## Project Structure

```

java/
   ├── MainActivity3.java     # Sets up the ViewPager and attaches the adapter
   └── ImageAdapter.java      # PagerAdapter that supplies the slider images
layout/
   ├── activity_main3.xml # Layout containing the ViewPager (id: viewPage)
drawable/
     ├── pic
     ├── wallpaper
     ├── wallpaper2
     └── google             # Images shown in the slider
```

## How It Works

1. `MainActivity3` loads `activity_main3.xml` and finds the `ViewPager` (`R.id.viewPage`).
2. It creates an `ImageAdapter` and sets it on the `ViewPager`.
3. For each page, `ImageAdapter.instantiateItem()` builds an `ImageView` with the matching drawable and adds it to the pager.
4. When the user swipes, `destroyItem()` removes pages that are no longer visible, which keeps memory usage low.

## Customizing the Slider

To add or change images, put them in `res/drawable/` and update the array in `ImageAdapter.java`:

```java
private int[] sliderImageId = new int[]{
    R.drawable.image1, R.drawable.image2, R.drawable.image3
};
```

## Preview

<img width="702" height="1600" alt="image" src="https://github.com/user-attachments/assets/d299aebe-d71a-483c-a165-2c5a24c89007" />

## On Sliding

<img width="702" height="1600" alt="image" src="https://github.com/user-attachments/assets/dbe7f94e-33a4-4710-8d0e-ab192516675e" />

## After Sliding (New Image Appears)

<img width="702" height="1600" alt="image" src="https://github.com/user-attachments/assets/d54f0fe0-9a58-469f-a42a-dcabc3fe46c9" />



## Tech Stack & Dependencies

- **Language:** Java / XML
- **IDE:** Android Studio
- **Libraries:**
  - `androidx.viewpager` (`ViewPager`, `PagerAdapter`)
  - `androidx.appcompat`, `androidx.activity`, `androidx.core`

## Requirements

- Android Studio (latest stable version recommended)
- Android SDK with an emulator or physical device (API 21+, adjust to your `minSdk`)
- Java 8+

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/Alveeza-Ilyas/Mobile-App-Image-Slider-with-ViewPager
   ```
2. Open **Android Studio**.
3. Select **Open an Existing Project** and choose the cloned folder.
4. Wait for the Gradle sync to finish.
5. Press **Run** (`Shift + F10`) on an emulator or physical device.

## Notes

- `ViewPager` is the older paging component. For new projects, `ViewPager2` is the recommended replacement.
- Package name: `com.alveezailyas.myhomework`

## Author

**Alveeza Ilyas**
