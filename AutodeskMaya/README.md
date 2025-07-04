# Autodesk Maya Recipes

This directory contains AutoPkg recipes for deploying Autodesk Maya via Munki.

## Files

- `Maya.pkg.recipe` - Creates a package with network licensing support
- `Maya.munki.recipe` - Imports Maya package into Munki repository

## Usage

These recipes are designed to be used with recipe overrides for security. The base recipes contain no sensitive information.

### Required Override Variables

Create local recipe overrides with these required variables:

- `VERSION_YEAR` - Maya version year (e.g., "2025")
- `PRODUCT_KEY` - Maya product key
- `NETWORK_SERVERS` - Comma-separated list of license servers (e.g., "@server1.domain.com,@server2.domain.com")

### Example Override

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Identifier</key>
    <string>local.pkg.Maya.YourOrg</string>
    <key>Input</key>
    <dict>
        <key>VERSION_YEAR</key>
        <string>2025</string>
        <key>PRODUCT_KEY</key>
        <string>YOUR_PRODUCT_KEY</string>
        <key>NETWORK_SERVERS</key>
        <string>@license1.yourdomain.com,@license2.yourdomain.com</string>
    </dict>
    <key>ParentRecipe</key>
    <string>com.github.kkeilson.pkg.Maya</string>
</dict>
</plist>
```

## Security Note

**Never commit recipe overrides containing sensitive information to public repositories.** Store them locally in `~/Library/AutoPkg/RecipeOverrides/` or in a private repository.
