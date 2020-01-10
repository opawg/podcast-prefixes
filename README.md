# podcast-prefixes
A JSON list of podcast prefix companies

If you have the URL of a podcast's audio file, this JSON file will help you work out whether there is a podcast prefix company being used for analytics, and be able to link to their privacy policy

## Contributing to the list

For now, the simplest way is to add to the file at `src/prefixes.json`. Each podcast host may have multiple entries, but the URL patterns should be unique.

Each entry _must_ contain the following properties:

* `prefixpattern`: a unique string to spot within the audio URL. It may not always be first, when companies chain URLs.

* `prefixname`: a humanly-readable name of the prefix company

* `prefixurl`: a website link (escaped) that links to the homepage of the podcast prefix company.

* `prefixprivacyurl`: a website link (escaped) that links to the privacy policy of the podcast prefix company.

## Code sample

This would probably work:

```$stmt = $db->prepare("SELECT * FROM `podcasts-prefixes` WHERE INSTR(:url,pattern) LIMIT 1");   
$stmt->execute(array(':url'=>$podcast['audiourl']));   
$prefix = $stmt->fetch(PDO::FETCH_ASSOC);```

Improvements are welcome.
