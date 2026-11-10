# Fading West · 2026 Social Media Schedule

Static site with Fading West's scheduled social posts, one page per calendar week. Each week page previews every post in Instagram, Facebook and LinkedIn layouts (mobile and desktop), with captions and the final files to download.

```
index.html                          landing page: weeks grouped by month (add a card for each new week)
2026-11_week-1_11-04-to-11-06/      Nov. 4–6
2026-11_week-2_11-09-to-11-13/      Nov. 9–13
2026-11_week-3_11-16-to-11-20/      Nov. 16–20
2026-11_week-4_11-27/               Nov. 27
2026-12_week-1_12-02/               Dec. 2
  [folder name].html                the week's page (same name as its folder)
  pv/                               preview images used by the mock-ups
  *.png, *.jpg, *.mp4               final post files
render.yaml                         Render static-site blueprint
```

Folder names: `[year]-[month]_week-[week of the month]_[first post date]-to-[last post date]` (one date when the week has one post). Week 1 is the first week with a weekday in that month (Nov. 2, Nov. 30 for December).
The "Calendar in SharePoint" button on each week page opens the team calendar in SharePoint (2026_SocialCalendar.xlsx, Marketing Team site); viewers need Fading West SharePoint access.
The navy bar at the top of each week page links back to the landing page and to the previous and next weeks.

No build step. Everything is plain HTML, CSS and JavaScript. Fonts load from Google Fonts and the zip download uses JSZip from cdnjs.

## Deploy on Render

These files go at the **top level** of the repository: `index.html`, `render.yaml` and the week folders sit at the root, not inside another folder.

1. In Render, open the static site, then **Settings**:
   - **Root Directory:** leave blank.
   - **Build Command:** `echo "No build step"`
   - **Publish Directory:** `.`
2. Under **Redirects/Rewrites**, delete any rules. The site needs none.
3. Save and choose **Manual Deploy → Clear build cache & deploy**.

The home page is the landing page. Each week's page is at `/[folder]/[folder].html`, for example `/2026-11_week-2_11-09-to-11-13/2026-11_week-2_11-09-to-11-13.html`.

## Access

A Render static site is public to anyone with the URL. The pages ask search engines not to index them (`noindex`), but that does not restrict access. Some posts still have open items (photo releases, the DHHL announcement, figures pending Ops). Share the link only with people who should see unreleased content.

## Preview locally

```
python3 -m http.server 8000
```
Then open http://localhost:8000. Opening the HTML files directly from disk also works, except the zip downloads, which need a web server.
