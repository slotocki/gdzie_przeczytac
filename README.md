# Gdzie przeczytać — Where to Read

**A non-commercial engineering thesis project about comparing ebook and audiobook subscriptions in Poland.**

Gdzie przeczytać is a planned web application that helps readers find books across subscription services and compare how well those services cover their reading interests. The project combines catalogue integration, bibliographic record matching, and an explainable scoring model.

**Status:** research and development in progress. Google Trends integration is a proposed experiment, subject to approval for the Google Trends API alpha. The descriptions below distinguish planned functionality from research objectives.

## Project objectives

- Search for books by title, author, or ISBN.
- Group editions and recordings that represent the same literary work while preserving their language and format information.
- Distinguish subscription access from individual purchases and free alternatives.
- Compare subscription catalogues using transparent scoring rules.
- Explain which books and criteria contribute to each subscription's score.

The intended scope is a catalogue on the order of 50,000 records. Multiple editions of the same work should not receive duplicate points. Availability is evaluated for a specific subscription plan, language, format, and observation date.

## Baseline ranking model

The initial model assigns a base score to an available work and adds bonuses for popular categories, authors frequently mentioned in Polish readership reports, a confirmed Polish Wikipedia article about the work, sufficiently supported Open Library ratings, availability unique to the compared subscriptions, and access in both ebook and audiobook formats.

A multiplier reduces the contribution of works with a confirmed comparable free alternative in Wolne Lektury. The weights are research assumptions to be evaluated, rather than an established measure of book quality or market popularity.

## Proposed use of the Google Trends API

The research would investigate whether search interest in books and authors can provide a useful additional signal for comparing Polish subscription catalogues.

The main questions are:

1. How many books in a representative sample have usable search-interest data for Poland?
2. How reliably can queries distinguish a book from its film adaptation, an unrelated meaning of the title, or the author as a whole?
3. How do seasonal patterns, including interest associated with school reading, affect the signal?
4. Does adding search-interest data materially change subscription rankings compared with the baseline model?

Google Trends data would be interpreted as relative search interest, not as absolute search counts, sales figures, or confirmed readership.

## Initial experiment

The proposed pilot would start with **200–500 books**, selected across categories and popularity levels, including Polish works and translated literature.

- **Geography:** Poland.
- **Historical window:** approximately 24–36 months.
- **Aggregation:** weekly or monthly, depending on data coverage and the experimental question.
- **Query design:** evaluate title and author combinations and manually inspect ambiguous cases.
- **Evaluation:** measure coverage, investigate missing or low-volume results, compare the signal with existing indicators, and assess changes in subscription rankings.
- **Collection:** use a scheduled research workflow rather than making external API calls for every user search.

Expansion beyond the pilot would depend on observed coverage, API quotas, access conditions, and the usefulness of the signal. The full catalogue size does not imply that all records would be queried immediately.

## Feedback for the alpha programme

The pilot would provide practical feedback on query ambiguity, coverage of Polish book titles, comparisons across requests, historical aggregations, and integration difficulties. Findings and reproducible issue descriptions could be shared with the Google Trends team by email.

## Data sources under consideration

| Source | Intended role |
|---|---|
| Subscription providers | Catalogue records and evidence of availability in particular plans. |
| Biblioteka Narodowa | Bibliographic metadata and Polish readership reports. |
| Wikidata and Polish Wikipedia | Identification of works and confirmation of corresponding articles. |
| Open Library | Work and edition identifiers, ratings, and optional reader-interest indicators. |
| Wolne Lektury | Identification of comparable free ebook or audiobook alternatives. |
| Google Trends API alpha | Proposed experimental search-interest signal, if access is granted. |

Source observations and matching decisions should be traceable. Missing metadata or an unsuccessful match should be recorded separately from a confirmed absence. Subscription availability should be established from offer data, rather than inferred from bibliographic sources.

## Planned technology

- **Backend:** C# and ASP.NET Core.
- **Frontend:** React with TypeScript.
- **Database:** PostgreSQL.
- **Data processing:** scheduled imports, bibliographic matching, and locally calculated ranking scores.

## Academic scope

This is an individual engineering thesis project with a non-commercial research purpose. The intended outcomes are a prototype application, a documented integration and matching methodology, and an evaluation of the ranking model and its limitations.

## References

- [Google Trends API alpha programme](https://developers.google.com/search/apis/trends)
- [Google Trends API announcement and data description](https://developers.google.com/search/blog/2025/07/trends-api)
- [Biblioteka Narodowa bibliographic API](https://data.bn.org.pl/docs/bibs)
- [Biblioteka Narodowa readership reports](https://www.bn.org.pl/raporty-bn/stan-czytelnictwa-w-polsce/)
- [Wikidata WikiProject Books](https://www.wikidata.org/wiki/Wikidata:WikiProject_Books)
- [Open Library API documentation](https://openlibrary.org/developers/api)
- [Open Library data dumps](https://openlibrary.org/developers/dumps)
- [Wolne Lektury API](https://wolnelektury.pl/api/)
