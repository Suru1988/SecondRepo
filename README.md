Terraform - local_file (Resource)
Generates a local file with the given content.

Note about resource behaviour
When working with local files, Terraform will detect the resource as having been deleted each time a configuration is applied on a new machine where the file is not present and will generate a diff to re-create it. This may cause "noise" in diffs in environments where configurations are routinely applied by many different users or within automation systems.

Note about file content
File content must be specified with exactly one of the arguments content, sensitive_content (Deprecated), content_base64, or source.

Note
If the file content is sensitive, use the local_sensitive_file resource instead.

Example Usage
resource "local_file" "foo" {
  content  = "foo!"
  filename = "${path.module}/foo.bar"
}
Copy
Schema
Required
filename (String) The path to the file that will be created. Missing parent directories will be created. If the file already exists, it will be overridden with the given content.
Optional
content (String) Content to store in the file, expected to be a UTF-8 encoded string. Conflicts with sensitive_content, content_base64 and source. Exactly one of these four arguments must be specified.
content_base64 (String) Content to store in the file, expected to be binary encoded as base64 string. Conflicts with content, sensitive_content and source. Exactly one of these four arguments must be specified.
directory_permission (String) Permissions to set for directories created (before umask), expressed as string in numeric notation. Default value is "0777".
file_permission (String) Permissions to set for the output file (before umask), expressed as string in numeric notation. Default value is "0777".
sensitive_content (String, Sensitive, Deprecated) Sensitive content to store in the file, expected to be an UTF-8 encoded string. Will not be displayed in diffs. Conflicts with content, content_base64 and source. Exactly one of these four arguments must be specified. If in need to use sensitive content, please use the local_sensitive_file resource instead.
source (String) Path to file to use as source for the one we are creating. Conflicts with content, sensitive_content and content_base64. Exactly one of these four arguments must be specified.
Read-Only
content_base64sha256 (String) Base64 encoded SHA256 checksum of file content.
content_base64sha512 (String) Base64 encoded SHA512 checksum of file content.
content_md5 (String) MD5 checksum of file content.
content_sha1 (String) SHA1 checksum of file content.
content_sha256 (String) SHA256 checksum of file content.
content_sha512 (String) SHA512 checksum of file content.
id (String) The hexadecimal encoding of the SHA1 checksum of the file content.
