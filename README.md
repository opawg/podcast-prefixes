# podcast-prefixes
A JSON list of podcast prefix companies

If you have the URL of a podcast's audio file, this JSON file will help you work out whether there is a podcast prefix company being used for analytics, and be able to link to their privacy policy

## Contributing to the list

For now, the simplest way is to add to the file at `src/prefixes.json`. Each podcast host may have multiple entries, but the URL patterns should be unique.

Each entry _must_ contain the following properties:

* `prefixpattern`: a unique string to spot within the audio URL. It may not always be first, when companies chain URLs.

* `prefixname`: a humanly-readable name of the prefix company

* `abilities_stats`: a boolean showing whether this prefix company uses its logs to provide stats

* `abilities_tracking`: a boolean showing whether this prefix company uses its logs to provide tracking and attribution

* `abilities_dynamicaudio`: a boolean showing whether this prefix company is capable of dynamic content insertion, used for advertising or content.

* `prefixurl`: a website link (escaped) that links to the homepage of the podcast prefix company.

* `prefixprivacyurl`: a website link (escaped) that links to the privacy policy of the podcast prefix company.

## Code sample

Podnews uses this:

```$stmt = $db->prepare("SELECT * FROM `podcasts-prefixes` WHERE INSTR(:url,prefixpattern)");
$stmt->execute(array(':url'=>$podcast['audiourl']));
$prefixes = $stmt->fetchAll(PDO::FETCH_ASSOC);```

Of note: some podcasts are measured by multiple prefix providers.

Improvements are welcome.
