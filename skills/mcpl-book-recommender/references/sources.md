# Source registry and routing

Open relevant source pages and record author/title, URL, date, evidence type and why the pick is supported. Access varies by runtime; use alternatives if blocked. Avoid duplicated/syndicated endorsements. The following sources are starting points, not guarantees of access.

| Source | Evidence and access | URL |
| --- | --- | --- |
| NPR Books We Love | Editorial/critic picks for fiction, nonfiction, kids and YA; filter topic and year | https://apps.npr.org/best-books/ |
| NY Times Books | Category bestseller rankings and separately published reviews; public web or keyed Books API for lists | https://www.nytimes.com/books/best-sellers/ ; https://developer.nytimes.com/ |
| Kirkus Reviews | Professional reviews and best-book selections across audiences; public portions | https://www.kirkusreviews.com/ |
| Publishers Weekly | Industry reviews and editorial lists; public portions | https://www.publishersweekly.com/ |
| Book Riot | Thematic and genre lists, new books across audiences; public web | https://bookriot.com/ |
| National Book Foundation | National Book Awards, fiction, nonfiction, translated literature, poetry and young people's literature | https://www.nationalbook.org/ |
| Pulitzer Prizes | Fiction, history, biography, nonfiction, poetry winners/finalists | https://www.pulitzer.org/prize-winners-by-year |
| Booker Prizes | Literary fiction and translated fiction awards and lists | https://thebookerprizes.com/ |
| ALA / ALSC | Children's librarian lists, Newbery, Caldecott, Geisel, Sibert, notables | https://www.ala.org/alsc/book-lists |
| Reading Rockets | Curated children's age/format/topic lists | https://www.readingrockets.org/books-and-authors/books |
| The Horn Book | Professional children's/YA reviews and selections; public portions | https://www.hbook.com/ |
| LibraryThing | Read-alikes via public work pages or keyed Multi-Recommendations API | https://www.librarything.com/developer/documentation/multirecommendations |
| NoveList Plus / K-8 Plus | Licensed librarian booklists, appeal factors and read-alikes; use only authorized access | https://about.ebsco.com/novelist |
| Goodreads | Public reader opinions and lists; no assumed API access; no scraping | https://www.goodreads.com/ |
| Reddit | Public community recommendations; anecdotal evidence, not professional review | https://www.reddit.com/r/suggestmeabook/ |
| TasteDive | Optional public read-alike leads; legacy API deferred | https://tastedive.com/read/api |
| Google Books | Bibliographic metadata, not recommendation endorsement; API | https://developers.google.com/books/docs/v1/using |
| Open Library | Work/edition identity, ISBN, subject, low-volume metadata API | https://openlibrary.org/dev/docs/api/search |
| Subject experts / publishers | University syllabi, professional associations, expert reading lists and publisher edition details; choose according to topic and cite exact pages | Use relevant official sites |

## Routing

- General browsing: NPR + Kirkus/Publishers Weekly + award or librarian/editorial lists. Use NYT as one popularity signal, not the entire candidate pool.
- Fiction and genre: NPR genre filters + Kirkus or Book Riot + relevant award or read-alike source; consider Booker or National Book Awards when relevant.
- Nonfiction/history/biography: NPR + professional reviews + relevant Pulitzer/National Book Award lists; check expertise and evidence.
- Technical learning and business: university or expert reading lists + independent reviews + publisher edition details; distinguish fundamentals from time-sensitive technologies. Avoid recommending obsolete editions unless useful historically.
- New releases: dated editorial/review lists + NYT category if relevant; verify publication dates and that lists are current.
- Read-alikes: LibraryThing or authorized NoveList + professional thematic lists and community discussion. Resolve seed ISBN first.
- Children: ALSC + Reading Rockets + Horn Book/NPR/Book Riot; use Geisel for beginning readers, Newbery for middle grade, Sibert for nonfiction; check actual suitability.
- Teens/YA: age-targeted professional and librarian lists, e.g. ALA YALSA (https://www.ala.org/yalsa/) + Horn Book/NPR/Book Riot. Distinguish YA from adult books with teenage protagonists.
- Classics/awards/book clubs: official award records + NPR or relevant professional/librarian lists. For translated books verify translator and language edition.
- When a source fails, substitute an independent professional or librarian source and disclose the gap.

## Optional API helper

From the skill directory, run Python 3 (standard library only). Each invocation makes one read-only request. Use environment variables NYT_BOOKS_API_KEY, LIBRARYTHING_API_KEY or GOOGLE_BOOKS_API_KEY as needed; set OPEN_LIBRARY_CONTACT to an application contact email for regular Open Library use. Never print or commit keys. Read provider terms before enabling access. API JSON is evidence or metadata, not the final ranking.

    python scripts/book_api.py openlibrary 'The Three-Body Problem Cixin Liu'
    python scripts/book_api.py google 'intitle:The Three-Body Problem'
    python scripts/book_api.py nyt names
    python scripts/book_api.py nyt hardcover-nonfiction
    python scripts/book_api.py librarything 9780316381994

Use the NYT list names response to verify a current list slug. LibraryThing accepts comma-separated ISBNs; resolve recommended ISBNs through metadata before ranking. Its documented free usage is 25 requests/day and 1/sec; verify limits before using. Open Library should be queried at low volume (no more than 1/sec without identification). Google Books quota/key requirements may vary. If an API returns an error, even in an HTTP 200 JSON response, use authorized web sources instead. Never retry around access blocks. NoveList and TasteDive are not API adapters in this version.

## Library fulfillment (default MCPL)

- Physical catalog: https://mcpl.aspendiscovery.org/
- Digital catalog: https://mcplmd.overdrive.com/ (Libby by OverDrive).
- MCPL resources: https://mcpl.aspendiscovery.org/WebBuilder/ResourcesList (NoveList Plus, NoveList K-8 Plus, Hoopla and other licensed resources; authorized access only).
- For a specific branch, inspect the actual catalog record for title, author, edition, format, branch, status and call number. Do not infer current shelf status from search snippets or a record's existence. If a title is not found, state search scope; if access fails, mark unverified. Only use observed record URLs, or provide catalog homepage as fallback. Do not assume an authenticated catalog API exists. Other public libraries are supported when specified; discover their official catalog first.
