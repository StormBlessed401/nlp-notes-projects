dropna() removes rows where the value is actually a missing value — i.e., np.nan (Not a Number) — not just a string that looks like "NaN" or an empty string "".

| Value in DataFrame  | Is it dropped by `dropna()`? | Why?                               |
| ------------------- | ---------------------------- | ---------------------------------- |
| `np.nan`            | ✅ Yes                        | True missing value                 |
| `None`              | ✅ Yes                        | Interpreted as missing             |
| `""` (empty string) | ❌ No                         | It’s still a string                |
| `"NaN"` (string)    | ❌ No                         | It’s just a string, not a real NaN |
