# Go Live Cheatsheet

### Get Current Site Data
- Download the development site in full, including all uploaded files, to your local machine.
- Export the database connected with the development site.

### Commit and push
- Make final commit(s) with any changes that were pulled from the development site.
- Tag the last commit as the launch release.

```bash
git tag -a Launch -m 'Go live'

# Push tags to remote repo
git push --tags
```

### Upload new site to temporary location
- Connect to the hosting account (and set up Docksend in Transmit).
- Create a folder called `new-site` or something similar and upload all website files to this folder.
    - Make sure to include `.htaccess` files.
    - DO NOT include `.git` folder.
- While these files are uploading, connect to the database and import the new tables. If existing data is present, export it to your desktop.
- Update database.php to the new configuration and ensure it's working.
- Make the following folders writable. Try `755` first, if still not writable, use `777`:
    - `/app/tmp/*`
    - `/app/webroot/uploads/*`

### Back up old website
- Back out of the `new-site` folder and create a new folder named ".old-site-[date]" and move all of the old website files to this folder EXCEPT:
    - `/phpMyAdmin`
    - `/stats`
    - `/appies`
    - `/appiesnet`
- If you created an export of existing data in the live DB, upload that file into this folder as well.

### Go live with new website
- Go into your `new-site` folder and move all files out into the root directory.

### Post-launch Testing
- Login to the CMS and edit a page.
- Upload an image through CKEditor, save and edit again to make sure the paths wrote correctly.
- Test all forms and ensure they are going to the right location.
