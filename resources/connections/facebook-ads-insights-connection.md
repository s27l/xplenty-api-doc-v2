### Facebook Ads Insights Connection Attributes

|Name|Read-Only?|Required?|Default|Description|
|----|---------|---------|-------|-----------|
|id|Y| | |the connection's numeric identifier
|type|Y| | |`facebookadsinsights`
|name|N|Y| |the descriptive name given to the connection
|username|N|N| |the username
|password|N|Y unless code is provided| |the token
|unique_id|Y| | |the unique connection's identifier
|created_at|Y| | |the date and time the connection was created
|updated_at|Y| | |the date and time the connection was last updated
|refresh_token|N|N| |token used for refreshing
|uid|N|N| |the unique user id
|expires|N|N| |determines if connection should expire
|expires_at|N|N| |expiration time for oauth key
|code|N|N| |OAuth code parameter
|redirect_uri|N|Y if code is provided| |OAuth redirect URI used for code generation
|url|Y| | |the connection resource URL (API)
