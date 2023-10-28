---
title: Customize Your PowerShell Profile
tags:
  - Terminal
  - TerminalTipTuesday
  - PowerShell
  - profiles
  - customization
---
# Introduction
A PowerShell profile is a script that runs every time you start PowerShell and allows you to configure various aspects of your shell environment. You can use it to change the appearance of your console, load modules and scripts, create aliases and functions, and much more. By creating your own PowerShell profile, you can tailor PowerShell to your preferences and needs. In the following sections, I will explain how to create a PowerShell profile, what are the different types of profiles available, and how to add some useful customizations to your profile. Let’s get started!

# Profile Basics

## What is a Profile
A PowerShell profile is a script that runs when PowerShell starts. You can use the profile as a startup script to customize your environment. You can add commands, aliases, functions, variables, modules, PowerShell drives and more. You can also add other session-specific elements to your profile so they’re available in every session without having to import or re-create them. PowerShell supports several profiles for users and host programs. However, it doesn’t create the profiles for you. You need to create the profile files and directories manually or by using a command.

## Locating your Profile
To view where your default profile is located, use this command:

```PowerShell
$profile
```

Which should output something like this:

```output
C:\Users\griff\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

## Editing your profile
Ultimately your profile can be edited via any means you'd use to edit a text file. You can browse to the location printed to the terminal when you use `$profile` and open that file in your favorite editor. This might be something as simple and native as Notepad, something easy and third-party like the revered Notepad++, or a flow-blown ISE such as VS Code. If you have Vim or Nano installed on your system, you can also use that to edit your profile directly in your terminal with `vim $profile` or `nano $profile` (this is my preferred method, but use whichever way works best for you)!

# Customize Your Prompt's Theme
One common thing that many people like to do is customize the theme of their shell prompt. This is the text which is displayed at the left of your terminal window, preceding where you would input your commands. The default prompt looks like this:

```example
PS C:\Users\griff > 
```

I've customized my prompt to look like this:
![[Pasted image 20231028082617.png]]

We have two major options for customizing the prompt. 

## Manual Customization
The easiest way is to write your own prompt in your profile by modifying the `prompt` function:

```PowerShell
# Custom shell prompt for Windows PowerShell profile
function prompt {
    "[$(Get-Date -format 'hh:mm:ss tt')] PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) ";
}
```

This will change your prompt to include the time and look more like this:

```example
[08:30:28] PS C:\Users\griff >
```

## Oh My Posh!
The other major option to customize your PowerShell prompt theme is made possible by the Oh My Posh prompt theme engine. You can install Oh My Posh several ways:
- Run `winget install JanDeDobbeleer.OhMyPosh -s winget` in PowerShell
- If you use the Scoop package manager, you can run `scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json` in Powershell
- Install from the Microsoft Store

Once you have it installed, you can select a theme from their [themes page]((https://ohmyposh.dev/docs/themes). Once you've picked a theme, you'll want to edit your PowerShell profile to utilize the theme. You can point the `oh-my-posh` command at the URL of the theme's configuration, or you can download that configuration and point `oh-my-posh` at the local file.

Using local path:
```
oh-my-posh init pwsh --config 'C:\Users\griff\jandedobbeleer.omp.json' | Invoke-Expression
```

Using online URL:
```PowerShell
oh-my-posh init pwsh --config 'https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/jandedobbeleer.omp.json' | Invoke-Expression
```

If you want to download an online theme locally, you can use this:

```PowerShell
Invoke-WebRequest -Uri 'https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/jandedobbeleer.omp.json' -OutFile 'C:\Users\griff\jandedobbeleer.omp.json'
```

And then you can use that local path in your configuration. Once you've added one of the above commands to your profile, save it and close/re-open your terminal, and you should see your newly themed shell prompt!

Be sure to check out the Oh My Posh documentation which is linked in the Additional Resources section of this blog post to learn about getting started in detail, and see all of the neat things you can do with it!

# Add Aliases and Functions
You can add custom aliases to your PowerShell profile as well. One that I always add is this:

```PowerShell
New-Alias -Name 'vi' -Value 'vim'
```

This means that I can use `vi` to edit files in-terminal instead of having to remember to use `vim`; this is a more comfortable experience from me since `vi` is what I use on Linux.

Additionally, you can add custom functions to your profile. Here's a fun one that uses the **wttr.in** GitHub project to get the weather (be sure to check out the project in the Additional Resources section at the end of this post):

```PowerShell
function Get-Weather {
	Invoke-RestMethod -Method GET -Uri 'https://wttr.in/cupertino?format=3'
}
```

With that addition, you can use `Get-Weather` to get your specified location's current weather forecast:

```output
cupertino: ☀️   +48°F
```

While this particular example might seem trivial, hopefully you can see just how helpful and flexible this can be!

# Working with Multiple Profiles
You might want to use multiple PowerShell profiles for different scenarios or purposes. For example, you might have a profile for the PowerShell console and another one for VS Code. Or you might have a profile for your personal use and another one for your work use.

Earlier we talked about using `$profile` to print the path to your current profile to the terminal. When working with multiple profiles, you can use `$profile.CurrentUserAllHosts` to return the path of the profile for the current user and all hosts.

If you want to create a new profile for all users on the current host, you can do:

```PowerShell
New-Item -Path $profile.AllUsersCurrentHost -ItemType File -Force
```

To load a different profile than the current one, you can use the dot sourcing operator followed by the path to the profile file:

```PowerShell
. $env:userprofile\Documents\other_profile.ps1
```

# Conclusion
In this post, we have learned how to use PowerShell profiles to customize our PowerShell environment and enhance our productivity. We have seen how to locate and edit the profile file, how to change the prompt theme using manual settings or Oh My Posh, how to add custom aliases and functions, and how to work with multiple profiles for different scenarios or purposes. PowerShell profiles are a powerful and flexible way to tailor PowerShell to our needs and preferences. By using them wisely, we can make our PowerShell experience more enjoyable and efficient. I hope that you found some bit of this blog post helpful!

# Additional Resources
- [Oh My Posh Documentation](https://ohmyposh.dev/docs/)
- [GitHub - chubin/wttr.in: :partly_sunny: The right way to check the weather](https://github.com/chubin/wttr.in)
- [about Profiles - PowerShell | Microsoft Learn](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.3)