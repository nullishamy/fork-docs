# Domains JSON file
To register a subdomain, you need to create a new JSON file in the `domains` directory through a pull request. For example, to register `example.is-a.dev`, you would create a file named `example.json` in the `domains` directory. The full path would be `domains/example.json`.

## Filename

**Note**: You can include `.` (dots) in your filename to register a sub-subdomain (e.g., `blog.example.is-a.dev`). However, each segment of your subdomain must meet the following criteria:

The filename:

- Must be alphanumeric, in lowercase, with dashes as separators. Using underscores as separators is also valid, but it's recommended to use dashes.
- Must be at least 2 characters.
- Must have a `.json` file extension.

### Examples of Invalid Filenames
- `a.json` (filename is less than 2 characters)
- `A.json` (filename contains uppercase letters)
- `a..json` (filename contains consecutive dots)
- `.a.json` (filename starts with a dot)
- `a .json` (filename contains a space)
- `a$.json` (filename contains a non-alphanumeric character)
- `a.json.json` (filename contains more than one `.json` extension)

### Examples of Valid Filenames
All the filenames below meet all the criteria. The reason in parentheses is just an example of one of the criteria they meet.

- `ab.json` (at least 2 characters long)
- `example.json` (alphanumeric and in lowercase)
- `blog.example.json` (includes dots to register a sub-subdomain)
- `my-blog.json` (uses dashes as separators, which is recommended)
- `my_blog.json` (valid, but it's recommended to use dashes instead of underscores as separators)
## Structure

### owner (required)
You need to specify some information about yourself here. This is so that you can be contacted if required.
In the owner object, the fields username and email are required. You can add more information in this object if you want.
```json
{
  "owner": {
    "username": "<github-username>",
    "email": "<email@address>"
  }
}
```
If you don't wish to share your email address here, please share your twitter or discord or any other social media account.
```json
{
  "owner": {
    "username": "<github-username>",
    "email": "",
    "twitter": "twitter-handle",
    "discord": "discord-user-id"
  }
}
```

### description
Describe your domain name and your usage. This is purely for documentation purpose and is optional.

### repo
This is a link to your website repository or your github account. This is purely for documentation purpose and is optional.

### record (required)
This section is where you specify the DNS records. The supported types are:

- `CNAME`
- `A`
- `AAAA`
- `URL`
- `MX`
- `TXT`

Below are some examples for the given record types:

- **CNAME** record: This must be a hostname (`something.tld`). It cannot be used in conjunction with any other record types. This is typically used to map your domain to a specific server.
```json
{
  "record": {
    "CNAME": "<github-username>.github.io"
  }
}
```
- **A** record: This must be a list of IPv4 addresses. These addresses point your domain to a specific server.
```json
{
  "record": {
    "A": [
      "192.0.2.1",
      "198.51.100.1",
      "203.0.113.1"
    ]
  }
}
```
- **AAAA** record: This must be a list of IPv6 addresses. Like the A record, these addresses point your domain to a specific server.
```json
{
  "record": {
    "AAAA": [
      "2001:0db8:85a3:0000:0000:8a2e:0370:7334",
      "2001:0db8:85a3:0000:0000:8a2e:0370:7335",
      "2001:0db8:85a3:0000:0000:8a2e:0370:7336"
    ]
  }
}
```
- **URL** record: This redirects your domain to another URL.
```json
{
  "record": {
    "URL": "https://my-other-website.com"
  }
}
```
- **MX** record: This must be a list of hostnames. These hostnames specify the mail servers that handle emails for your domain.
```json
{
  "record": {
    "MX": [
      "mx1.improvmx.com",
      "mx2.improvmx.com"
    ]
  }
}
```
- **TXT** record: This can be either a single string or a list of strings. TXT records are often used for various purposes, such as verifying domain ownership and ensuring email security.
```json
{
  "record": {
    "TXT": "Hello World!"
  }
}
```
```json
{
  "record": {
    "TXT": ["Hello", "World!"]
  }
}
```