# iso-hijri

[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![bundle][bundle-src]][bundle-href]
[![JSDocs][jsdocs-src]][jsdocs-href]
[![License][license-src]][license-href]

This is an implementation of an ISO 8601 equivalent for the Hijri calendar. It is based on the [Hijri Calendar](https://en.wikipedia.org/wiki/Islamic_calendar) and the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standard.

Since Hijri calendar is a lunar calendar, It was necessary to define a standard for it which has [different rules](#rules) than the Gregorian calendar.

These rules should apply to all Hijri calendars, and this is what this package is trying to achieve.

The implementation is an extension of the [`Calendar`](https://github.com/js-temporal/temporal-polyfill/blob/a44a1bb61c738a504023427c486ab0a315c7b9d3/lib/calendar.ts#L129C14-L129C22) class from [`Temporal`](https://github.com/js-temporal/temporal-polyfill)

# Rules

The rules proposed here must work with all types of Hijri Calendars, not only the tabular types. i.e., must also work with the Um Alqura calendar.

1. **Week Definition**: 
   - The week starts on Saturday, designated as day 1, and ends on Friday, designated as day 7.

2. **Weekday Numbering**: 
   - Days of the week are numbered sequentially from 1 (Saturday) to 7 (Friday).

3. **Year Length**: 
   - A 'short year' consists of 50 weeks, totaling 350 days.
   - A 'long year' consists of 51 weeks, totaling 357 days.

4. **Midweek Day**: 
   - Tuesday is always the middle day of the week, designated as day 4.

5. **First Week Identification**: 
   - The first week of the ISO Hijri year is identified by the inclusion of the 4th day of Muharram.

6. **4th Muharram Placement**: 
   - The 4th of Muharram occurs exclusively in the first ISO week of the year. 
   - It does not appear in any other weeks, such as the 51st or 2nd weeks.

7. **Week 51 Extension**: 
   - Week 51 may extend into the following year but only up to the 3rd of Muharram.

8. **Week 50 Limitation**: 
   - Week 50 does not extend into the following year. 
   - Its latest possible day is the 29th of Dhu al-Hijjah. 
   - In rare cases, like in the Umm al-Qura calendar, week 50 may extend to this date, after which week 1 of the next year begins.

9. **Date Placement in Weeks 51 and 1**: 
   - The dates of 30th Dhu al-Hijjah, and the 1st, 2nd, and 3rd of Muharram can only fall within week 51 of the ending year or week 1 of the starting year.
   - To determine the first week of the ISO Hijri year, locate the 4th of Muharram and identify the corresponding Saturday of that week. This Saturday marks the first day of the ISO week.

> **Note on Terminology**: 
> Within this ISO week day system, years are categorized as 'short' or 'long.' The terms 'leap' and 'common' years are not applicable.

### Installation

```bash
npm install iso-hijri
```


## License

[MIT](./LICENSE) License © 2023-PRESENT [Mohsen Alyafei](https://github.com/MohsenAlyafei) and [Al-Kawarizmi](https://github.com/khawarizmus)

<!-- Badges -->

[npm-version-src]: https://img.shields.io/npm/v/iso-hijri?style=flat&colorA=080f12&colorB=1fa669
[npm-version-href]: https://npmjs.com/package/iso-hijri
[npm-downloads-src]: https://img.shields.io/npm/dm/iso-hijri?style=flat&colorA=080f12&colorB=1fa669
[npm-downloads-href]: https://npmjs.com/package/iso-hijri
[bundle-src]: https://img.shields.io/bundlephobia/minzip/iso-hijri?style=flat&colorA=080f12&colorB=1fa669&label=minzip
[bundle-href]: https://bundlephobia.com/result?p=iso-hijri
[license-src]: https://img.shields.io/github/license/antfu/iso-hijri.svg?style=flat&colorA=080f12&colorB=1fa669
[license-href]: https://github.com/antfu/iso-hijri/blob/main/LICENSE
[jsdocs-src]: https://img.shields.io/badge/jsdocs-reference-080f12?style=flat&colorA=080f12&colorB=1fa669
[jsdocs-href]: https://www.jsdocs.io/package/iso-hijri
