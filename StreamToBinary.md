# Stream to Binary data
- When converting stream to binary data, we should use `StringDecoder` module.
- It handles multi bytes character much better.
- It also handle incomplete multi byte character.
- StringDecoder preserves the encoded character internally for incomplete character and once complete then it returns.
- The default `Buffer.toString` does not preserves the encoded character.
-
