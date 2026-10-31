# Deploy this site on Hostinger

This project builds to a static website. It does not need Node.js running on the server or a database. The production files are in `dist/`; upload the *contents* of that folder to the domain's `public_html` folder.

## Build and upload

From the project folder, run:

```sh
npm ci
npm run build
```

The build prepares the Unity game and PPMake assets and copies `public/.htaccess` into `dist/`. Upload all files inside `dist` (including hidden files such as `.htaccess`) to Hostinger's `public_html`. Keep the folder structure intact. You can upload a ZIP of the `dist` contents and extract it into `public_html`, or transfer the files with FTP. Do not upload the source repository or put the `dist` folder itself under `public_html`.

In hPanel, open **Websites → Manage site → Files → File Manager**, select the files for your domain, and upload/extract there. Hostinger's File Manager supports archives up to 100 GB; this site's current build is about 525 MB. The Unity game data file is about 378 MB, so visitors who open the game will download a large file.

## Domain and HTTPS

The domain being registered at Hostinger does not by itself provide web hosting. Add the domain to an active Hostinger Web Hosting plan, then make sure it is connected to that hosting website. Domains registered at Hostinger are commonly connected automatically once added to hosting; follow the domain connection prompt in hPanel if it appears. After the domain points to the hosting account, enable/verify the free SSL certificate in hPanel and use the HTTPS address.

## After upload

- Visit the domain over HTTPS.
- Refresh `/portfolio` and check that the portfolio loads.
- Visit `/start` and check the standalone start page.
- Open the Game section and allow time for its large Unity data file to load.
- Check browser developer tools' Network panel if the game fails. The Apache rules in `.htaccess` set MIME and encoding headers for Unity WebGL files; the hosting server must allow Apache rewrite and headers directives.

## Updating the site

Run `npm run build` again after changes, then replace the old files in `public_html` with the new contents of `dist`. Keep `public_html` free of an old `index.php` or default Hostinger placeholder page that could take precedence over `index.html`.

Hostinger's current instructions: [upload website files](https://www.hostinger.com/tutorials/how-to-upload-your-website/) and [File Manager basics](https://support.hostinger.com/en/articles/4548688-basic-actions-in-the-file-manager).
