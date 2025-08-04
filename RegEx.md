#What is re (regular expression)?

re is Python’s Regular Expressions module. It lets you search, clean, or manipulate text based on patterns.

#Why use it in NLP?
In text preprocessing, you often need to:
Remove URLs, numbers, special characters, extra spaces, etc AND
Replace or extract parts of text using specific rules.

Example:
text = "I loved this! Check it out: https://example.com"
cleaned = re.sub(r"http\S+", "", text)  # removes URL
print(cleaned)  # "I loved this! Check it out: "
So re is your go-to tool for text cleaning and pattern matching before feeding data into a model.



Common regular expression (re) Examples in NLP Preprocessing
1. Remove URLs
import re

text = "Great product! See details at https://www.amazon.com/product/12345"
cleaned = re.sub(r"http\S+|www\S+", "", text)
# Output: "Great product! See details at "
Use case: Many reviews contain links. These are noise for sentiment models.

2. Remove HTML tags
text = "Amazing <b>laptop</b> with <i>great battery</i>."
cleaned = re.sub(r"<.*?>", "", text)
# Output: "Amazing laptop with great battery."
Use case: Useful when scraping web content or reading from HTML sources.

3. Remove Special Characters / Punctuation
text = "This laptop is AWESOME!!! @#%$^"
cleaned = re.sub(r"[^a-zA-Z0-9\s]", "", text)
# Output: "This laptop is AWESOME"
Use case: Removes noise and irrelevant symbols before analysis.

4. Remove Numbers
text = "Battery lasted 12 hours and weighs 1.5 kg"
cleaned = re.sub(r"\d+", "", text)
# Output: "Battery lasted  hours and weighs . kg"
Use case: If you're not analyzing numerical info, numbers are often removed.

5. Lowercase All Text
text = "Loved It! AMAZING Service."
cleaned = text.lower()
# Output: "loved it! amazing service."
Not re, but usually used with it — ensures consistency in analysis.

6. Remove Extra Spaces
text = "This   product     is   great"
cleaned = re.sub(r"\s+", " ", text).strip()
# Output: "This product is great"
Use case: Ensures clean formatting.

7. Keep Only Letters (Remove Everything Else)
text = "Wow! 10/10 - would buy again :)"
cleaned = re.sub(r"[^a-zA-Z\s]", "", text)
# Output: "Wow would buy again"
Use case: Keeps only text relevant for word-based models like TF-IDF.

8. Extract Hashtags or Mentions (from tweets)
text = "I love this product! #happy #Amazon @support"
hashtags = re.findall(r"#\w+", text)
# Output: ['#happy', '#Amazon']

mentions = re.findall(r"@\w+", text)
# Output: ['@support']
9. Replace Emoji with Empty String
text = "Love it 😍🔥🔥🔥"
cleaned = re.sub(r"[^\w\s]", "", text)
# Removes emojis and punctuation
# Output: "Love it "
You can also use libraries like emoji to detect & convert emojis properly if needed.






***how does --> r"http\S+|www\S+" work?***
First, what does the r do?
The r before the string makes it a raw string literal.
It tells Python not to interpret backslashes (\) as escape characters.

Example:

Without r: "\\n" is interpreted as a newline.

With r: r"\\n" keeps it as two characters: \ and n.

Now let's break the pattern itself:
http\S+
http: Matches the literal characters http

\S+:

\S means "any non-whitespace character"

AND + means "one or more of the previous"

So http\S+ matches:
http://example.com
https://www.amazon.in/product/B08K2S1B56
httpXYZ123 (basically anything starting with http followed by non-space characters)

| (pipe symbol)
Acts as OR

So we are saying:
-->match anything that looks like http...
OR
-->match anything that looks like www...

#www\S+
Same logic:

www = match the literal string "www"

\S+ = match all non-space characters that come after it

Matches things like:

www.google.com

www.amazon.in/product/XYZ




***** Putting it all together*****
When used like this:

cleaned = re.sub(r"http\S+|www\S+", "", text)
It means:

"In the text, find any substring that starts with http or www and continues until the next space, and replace it with an empty string (i.e., remove it)."



***FINAL EXAMPLE***
import re

text = "This product is awesome! Check it here: https://www.amazon.com/item123 or www.amazon.in/item456"
cleaned = re.sub(r"http\S+|www\S+", "", text)

print(cleaned)

OUTPUT:
This product is awesome! Check it here: 


***USE TABLE***


| Task                        | Regex Code          |           |
| --------------------------- | ------------------- | --------- |
| Remove URL                  | \`r"http\S+         | www\S+"\` |
| Remove HTML                 | `r"<.*?>"`          |           |
| Remove special chars        | `r"[^a-zA-Z0-9\s]"` |           |
| Remove numbers              | `r"\d+"`            |           |
| Remove extra whitespace     | `r"\s+"`            |           |
| Extract hashtags            | `r"#\w+"`           |           |
| Remove everything but words | `r"[^a-zA-Z\s]"`    |           |

#Use of RE in FEATURE ENGINEERING:
In Feature Engineering
You use re to extract meaningful patterns or features from raw data, especially text.

Examples of Feature Engineering using re:
Extract hashtags, mentions, or URLs

df['hashtags'] = df['tweet'].str.findall(r'#\w+')
Create a feature: "has email address?"

df['has_email'] = df['text'].str.contains(r'\S+@\S+')
Count number of digits in a string

df['digit_count'] = df['text'].str.count(r'\d')
Extract years or specific formats

df['year_mentioned'] = df['text'].str.extract(r'(19\d{2}|20\d{2})')
Flag presence of specific keywords or patterns

df['contains_warning'] = df['text'].str.contains(r'\b(warning|alert|caution)\b', flags=re.IGNORECASE)


<img width="1026" height="718" alt="image" src="https://github.com/user-attachments/assets/669532ee-7ff9-4264-8d39-13c267271a7d" />







