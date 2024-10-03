    # Process photos
    for photo in photos:
        file_path = os.path.join(download_folder, photo.filename)

        # Download the photo
        print(f"Downloading {photo.filename}...")
        with open(file_path, 'wb') as file:
            file.write(photo.download().raw.read())
        print(f"{photo.filename} downloaded successfully.")

        try:
            # Upload the photo to OneDrive
            upload_file_to_onedrive(access_token, file_path)

            # Delete the local file after successful upload
            if os.path.exists(file_path):
                os.remove(file_path)
                print(f"Deleted local file: {file_path}")

            # Delete from iCloud
            print(f"Deleting {photo.filename} from iCloud...")
            photo.delete()
            print(f"Deleted {photo.filename} from iCloud")

        except Exception as e:
            print(f"Error processing {photo.filename}: {e}")
