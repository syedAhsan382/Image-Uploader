# Image Uploader

A simple image uploader built with plain HTML, CSS, and JavaScript. Drag and drop images (or browse for them), see a preview card for each one with a progress bar, and keep them saved in the browser even after refreshing the page.

**🔗 Live Demo:** https://image-uploader-delta-flax.vercel.app 

> **Note:** This is a front-end practice project. Nothing is sent to a server. The progress bar is simulated, and images are stored in the browser's `localStorage`.

<!-- Add a screenshot or GIF of the app here: -->
![Image Uploader processing image file](https://github.com/syedAhsan382/Image-Uploader/blob/e3a97cfde39a6d870641266c45e8f5dee48c3c27/Image-uploader.png) 

## Features

- Drag and drop images onto the drop zone, or click to browse your files
- Upload multiple images at once
- Accepts **JPG, PNG, and GIF** only
- Validates each file (MIME type, file extension, and size up to 2MB)
- Shows an error message for invalid files, which disappears after 5 seconds
- Preview card for each image with its name and size
- Simulated progress bar (built with `setTimeout`)
- Images are saved in `localStorage`, so they are still there after a refresh
- Remove a single image, or clear all images at once
- Responsive layout that works on smaller screens

## Built With

- **HTML5**: page structure and the hidden file input
- **CSS3**: custom properties (variables), Flexbox, CSS Grid, transitions, and keyframe animations
- **JavaScript (ES6)**: DOM manipulation, `FileReader`, `localStorage`, and `setTimeout`

No frameworks or libraries are used.

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```
2. Open the project folder.
3. Open `index.html` in your browser. No install or build step is needed.

## Project Structure

```
image-uploader/
├── index.html    # Page structure
├── style.css     # All styling
└── script.js     # App logic
```

## How It Works

1. The user drops files on the drop zone or selects them with the file picker.
2. Each file goes through `validateAndProcess()`, which checks the type, extension, and size.
3. If the file is valid, `processFile()` creates a preview card and reads the file with `FileReader.readAsDataURL()`.
4. `simulateUpload()` fills the progress bar using a function that keeps scheduling itself with `setTimeout`.
5. When the bar reaches 100%, the image is saved to `localStorage` as a data URL.
6. When the page loads again, `loadFromStorage()` rebuilds the cards from the saved data.

## What I Learned

- Handling drag and drop events (`dragenter`, `dragover`, `dragleave`, `drop`) and why `preventDefault()` is needed
- Reading files in the browser with `FileReader`
- How `setTimeout` schedules a function to run later without pausing the rest of the code
- Saving and loading data with `localStorage`, including `JSON.stringify` and `JSON.parse`
- Changing styles by adding and removing CSS classes from JavaScript
- Building a responsive grid with `repeat(auto-fill, minmax(...))`

## Known Limitations

- `localStorage` holds only about 5MB, so a few images can fill it up. Data URLs are also about 33% larger than the original file.
- If you remove an image while it is still "uploading", it can reappear after a refresh, because the progress loop keeps running and saves it when it finishes.
- File names are inserted into the card with `innerHTML`, so a file name containing HTML characters could break the card. Using `textContent` would be safer.

## Possible Improvements

- Fix the remove-while-uploading bug by stopping the progress loop when the card is removed
- Use `textContent` instead of `innerHTML` for file names
- Connect to a real backend so uploads are actually stored
- Use IndexedDB instead of `localStorage` for larger storage
- Add image compression before saving

## Author

**Ahsan**

- GitHub: [syedAhsan382](https://github.com/syedAhsan382)
- LinkedIn: [Syed Ahsan](https://www.linkedin.com/in/syed-muhammad-ahsan-263ab8351)

## License

This project is open source and available under the [MIT License](LICENSE).
