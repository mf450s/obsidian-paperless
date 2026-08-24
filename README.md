# Obsidian ❤️ Paperless-ngx

This plugin allows users to easily insert links to documents from their self-hosted paperless-ngx instance into their Obsidian notes. It creates or reuses a Paperless share link and inserts a normal Markdown link; document binaries are never stored in the vault.

## Features

- View all documents on your paperless-ngx instance from within the comfort of your Obsidian vault.
- One-click insertion of one or many documents into your vault.
- Keep your vault small by referencing documents through Paperless share URLs.

## Prerequisites 
This assumes you have a working version of [paperless-ngx](https://github.com/paperless-ngx/paperless-ngx) hosted. It does not necessarily need to be remotely accessible. This decision is left up to the reader. 

## How it works
This plugin interacts with your Paperless instance to enable quick linking from Obsidian. When you click on a document to insert it, the plugin fetches a valid share link or creates one when needed, then inserts Markdown such as `[Paperless document](https://paperless.example/share/...)`. No PDF file, dummy or otherwise, is created in the vault.

## Setup

**Paperless-ngx**

1. Obtain an authorization token for your account. Open the "My Profile" link in the user dropdown found in the paperless-ngx web UI. Copy the API Auth Token.

**Obsidian**

2. Install the plugin.
3. Fill in the following settings:
    - Paperless URL: full url to your paperless-ngx instance. Do not include the trailing `/`.
    - Paperless authentication token: token you obtained in step 1.
4. Click "Test connection" to confirm connectivity. If any errors appear, you can view them in the console. Open the console using `cmd+option+i` (MacOS) or `ctrl+shift+i` (Windows).

## Usage

### Basic usage
1. Go to the note you want to insert a document into. The editor view must be in focus.
1. Open the command palette in Obsidian (ctrl/cmd + p or swipe down on mobile).
1. Search "Paperless".
1. Select `Paperless: Insert document`. Click on the document(s) you want to insert.

### Available Commands
The following commands are available for use.

#### Insert document
The standard insertion command. Please note you must have an open editor focused to use this command. Brings up the document selection modal.

#### Refresh document cache
The "Insert document" command caches some information such as available documents, tags, and other metadata when it is first run. If you find that new documents or changes are not showing up in the document selection modal, running this command will refresh the caches.

#### Replace URL with document
This command replaces a URL in a note with a direct Paperless share link. It recognizes both Paperless URLs and legacy `[[paperless-ID.pdf]]`/`![[paperless-ID.pdf]]` references, and converts them without creating files. To use:
1. Move your cursor onto a paperless url in a note. The url should be of the form `http://ip:port/api/documents/id/preview/` or `http://ip:port/documents/id/details`
1. Run this command

## Manual testing
Test documents with multiple pages and documents with tags. Also test documents whose Paperless share links are missing.
