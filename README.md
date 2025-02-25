# prjctr-17-peak-loadings

Describe solution that solves peak loadings problem for biggest european football website https://goal.com:

1. Analyze all types of pages on the site.

2. Analyze and list possible sources of peak loadings.

3. Describe possible solution for each type.

## Types of the pages

- News
- Live scores
- Match results
- Information about the teams and players
- Static content

## Possible sources of the peak loadings

- External attacks
- Long polling / websocket auto-updated live scores of the current matches
- "Short polling", i.e. users actively checking a match results page
- Heavy users activity (during the matches or championships) on the 'main' and 'results' page
- Bot activity (like by the ones that help making bets on match results)

## Possible solutions

1. Since all the matches are scheduled, we can add system resources (i.e. scale) in advance, moreover - make scaling region-specific

2. Use existing solutions for DDoS protection, like AWS Shield or more advanced CloudFlare

3. Use CDN for the static content

4. We can actively use in-memory cache, especially on the pages that are not user-specific (i.e. not personalized), like the latest news or current match results

5. Limit well-behaved (Googlebot etc) bot access by configuring the `robots.txt`, static pages metadata, and/or nginx `X-Robots-Tag`
