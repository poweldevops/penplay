# penplay
Playpen repository.

## Testing, testing.
I seemed to have forgotten this vital piece of information.

## Conventions
We can haz conventions plz?

[palpawhine] : http://www.troll.me/images/grinning-emperor-palpatine/good-good-let-the-naming-convention-flow-through-you.jpg "Yeees... let it flow through you!"

### Function naming and format
All functions must begin with valid verbs and should contain enough "action"
words to make it fairly apparent what the function is about without becoming
too verbose (that's what the manpage information we preface the function body
with is for).

See ``` man about_Verbs ``` for information on valid powershell verbs.

```
function Verb-Action-Product {
  <#
  .Synopsis
  Short description of the Function
  .Description
  Extended, more explanatory description of the function.
  .InPuts
  [info]List of input and types
  .OutPuts
  [info]Output variable and type
  .Notes
  NAME: Verb-Action-Product
  AUTHOR: Your Name (you@powel.no)
  #>
  [CmdletBinding()]
  Param(
    [Parameter(Mandatory=$False)]$SomeParameter = 'DefaultValue'
  )
}
```

### Output
No output should ever be produced via Write-Host except strictly for debugging
purposes. Using it on branches for debugging purposes is OK, but this should not
be merged into master.

All output shall be written using Write-Verbose, Write-Warning, Write-Error
and Write-Debug. This is enabled through the use of ``` [CmdletBinding()] ```.

Functions can then be called with the -Verbose parameter if this output is deemed
useful at the time. Alternately the user can control this through the preference
variables ``` $VerbosePreference ```,``` $ErrorPreference ```, etc.

See ``` man about_Preference_Variables ``` .

### Sensitive information
Scripts should under no circumstances contain sensitive information, and the
location of any such information pulled on runtime should only come from
parameters to functions. Use module variables to keep and share the information.
