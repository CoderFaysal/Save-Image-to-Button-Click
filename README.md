# Save Image to Button Click

```
private void saveImageToGallery() {
        Drawable drawable = [image path].getDrawable();
        Bitmap bitmap = ((BitmapDrawable) drawable).getBitmap();
        String path = Environment.getExternalStorageDirectory().toString();
        File dir = new File(path + "/Pictures");
        dir.mkdirs();
        String fileName = "image_" + System.currentTimeMillis() + ".jpg";
        File file = new File(dir, fileName);
        try {
            FileOutputStream outputStream = new FileOutputStream(file);
            bitmap.compress(Bitmap.CompressFormat.JPEG, 100, outputStream);
            outputStream.flush();
            outputStream.close();
            MediaScannerConnection.scanFile(this, new String[]{file.getAbsolutePath()}, null, null);
            Toast.makeText(this, "Image saved to gallery", Toast.LENGTH_SHORT).show();
        } catch (IOException e) {
            e.printStackTrace();
            Toast.makeText(this, "Failed to save image", Toast.LENGTH_SHORT).show();
        }
    }
```
