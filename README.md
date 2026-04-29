# 🚀 File Downloader - Poo poo

· Download any file from anywhere directly into your GitHub repository
· Supports large files by splitting them into 90MB chunks (due to GitHub's limitations)

---

🔧 Installation Guide

1. Click the Fork button at the top of this repository
2. Change the fork name if needed, then click Create Fork
3. Your repository is ready! You can now download any file with a direct link into your repo, then download it to your system

---

🎯 How to Download Files to Your Repository

1. Prepare your direct link (e.g., example.com/files/something.zip)
2. Go to your GitHub and click on your forked repository, then select the Actions tab
3. In the Actions tab, you'll see a workflow named "Poo poo - Download from URLs & Save to Repo". Click on it, then click Run Workflow, enter your download link, and the download will begin...

---

📂 Where to Find Downloaded Files

All downloaded files are added to the downloads/ folder in your repository.

Files are split into 90MB chunks. For example:

· If your file is 300MB, you'll get 4 files
· Download all 4 files to your system
· Extract them using 7zip (Windows) or on Linux:

```bash
7z x file.zip
```

This will extract all split parts (file.zip, file.z01, file.z02, etc.) into a single folder.

---

⚙️ Available Settings

Setting Description Options
urls Space-separated list of URLs Any direct or YouTube link
mode Output mode normal (individual files) or zip (single archive)
split_threshold_mb Split files larger than this (0 = never split) Default: 90
youtube_format YouTube quality best, bestvideo+bestaudio, bestaudio, worst
output_name Custom filename pattern Use {date}, {id}, {title}
convert_format Convert to format keep, mp4, mkv, webm, mp3, m4a, wav, opus
batch_mode Batch processing sequential (one by one) or parallel (faster)
parallel_jobs Number of parallel downloads (1-5) Default: 3

---

🎬 Example Usage

Download a single YouTube video as MP3:

```
urls: https://youtube.com/watch?v=dQw4w9WgXcQ
youtube_format: bestaudio
convert_format: mp3
output_name: {date}_{title}
```

Download multiple files in parallel:

```
urls: https://example.com/file1.zip https://example.com/file2.mp4 https://youtube.com/watch?v=abc123
batch_mode: parallel
parallel_jobs: 3
```

Download, split, and zip:

```
urls: https://example.com/largefile.iso
mode: zip
split_threshold_mb: 90
```

---

📝 Output Name Placeholders

Placeholder What it becomes Example
{date} Date & time (YYYYMMDD_HHMMSS) 20250115_143022
{id} YouTube video ID dQw4w9WgXcQ
{title} Video title (sanitized) Rick_Astley_-_Never_Gonna_Give

Default pattern: {date}_{id}.ext

---

🧹 Cleaning Downloads

To delete all files in the downloads/ folder, use the "Poo poo - Clean Downloads Folder" workflow:

1. Go to Actions tab
2. Select "Poo poo - Clean Downloads Folder"
3. Type DELETE to confirm
4. Optionally choose to remove from git history (⚠️ permanent)

---

⚠️ Important Notes

· File splitting: Files larger than 90MB are automatically split for GitHub compatibility
· Reassembly: Use 7zip to merge split files back together
· Direct links only: For non-YouTube files, use direct download links
· YouTube: Supported with yt-dlp + Cloudflare WARP bypass
· Free tier limits: GitHub Actions has 6 hours/month on Ubuntu runners

---

🐛 Troubleshooting

Downloaded file shows as {title}.webm literally?

· Make sure you're using the latest workflow version
· The output_name should use placeholders like {date}_{id} not raw text

YouTube videos fail to download?

· The workflow includes Cloudflare WARP for IP bypass
· Try changing youtube_format to bestaudio or worst
· Some age-restricted videos may fail

Parallel downloads not working?

· Reduce parallel_jobs to 2 or 3
· Switch to sequential mode for problematic URLs

---
                                       ___________________
📞 Support                            |    GIVE   ME     |
                                       |   PLAYLIST DL   |
· Original project: AVASAM             __________________
· Forked version: Poo poo downloader    ___    |
thank you intellix senpai          ____/._.\___|
                                       \___/
                                       |   |
                                       |   |
---


than
