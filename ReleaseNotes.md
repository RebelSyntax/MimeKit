# Release Notes

### MimeKit 1.0.7

* Fixed TnefPropertyReader.GetEmbeddedMessageReader() to skip the Guid.
* When decrypting PGP data, iterate over all encrypted packets to find one that
  can be decrypted (i.e. the private key exists in the user's keychain).
* Updated WindowsSecureMimeContext to respect SecureMailboxAddresses like the
  other backends. (issue #100)
* Added a Pkcs9SigningTime attribute to the CmsSigner for WindowsSecureMimeContext.
  (issue #101)

### MimeKit 1.0.6

* Vastly improved MS-TNEF support. In addition to being fixed to properly extract
  the AttachData property of an Attachment attribute, more metadata is captured
  and translated to the MIME equivalents (such as attachment creation and
  modification times, the size of the attachment, and the display name).
* Migrated the iOS assemblies to Xamarin.iOS Unified API for 64-bit support.

Note: If you are not yet ready to port your iOS application to the Unified API,
      you will need to stick with the 1.0.5 release. The Classic MonoTouch API
      is no longer supported.

### MimeKit 1.0.5

* Fixed out-of-memory error when encoding some long non-ASCII parameter values in
  Content-Type and Content-Disposition headers.

### MimeKit 1.0.4

* Added workaround for msg-id tokens with multiple domains
  (e.g. id@domain1@domain2).
* Added convenience methods to Header to allow the use of charset strings.
* Added more HeaderList.Replace() method overloads for convenience.
* Added a FormatOptions property to disallow the use of mixed charsets when
  encoding headers (issue #139).

### MimeKit 1.0.3

* Improved MimeMessage.TextBody and MimeMessage.HtmlBody logic. (issue #87)
* Added new overrides of TextPart.GetText() and SetText() methods that take a
  charset string argument instead of a System.Text.Encoding.
* Fixed charset fallback logic to work properly (it incorrectly assumed that
  by default, Encoding.UTF8.GetString() would throw an exception when it
  encountered illegal byte sequences). (issue #88)
* Fixed S/MIME logic for finding X.509 certificates to use for encipherment.
  (issue #89)

### MimeKit 1.0.2

* Fixed MimeMessage.HtmlBody and MimeMessage.TextBody to properly
  handle nested multipart/alternatives (only generated by automated
  mailers).

### MimeKit 1.0.1

* Added MimeMessage.HtmlBody and MimeMessage.TextBody convenience properties.
* Added TextPart.IsPlain and TextPart.IsHtml convenience properties.