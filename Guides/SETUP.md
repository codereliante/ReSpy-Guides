<div align="center">
    <img src="https://cdn.discordapp.com/icons/1032763361806536805/7475550d0be2cd987ad6c0c0555005ec.webp?size=56" height="200" width="200">
    <h2>ReSpy</h2>
    <p align="center">
	<p>ReSpy— a paid seamless Discord utility bot.</p>
        </a> </p>
    </p>
</div>
    <a href="https://discord.gg/g4Z2Pbx">
        <img src="https://img.shields.io/discord/372036754078826496.svg">
    </a>
</p>


# Bloxlink Documentation
## Contents
* [Getting Started](#getting-started)
* [Nickname Templates](#nickname-templates)
* [Group Roles](#group-roles)
* [Permissions](#permissions)
* [Power Ups](#power-ups)
* [Command Usage](#command-usage)
* [Bloxlink Premium](#bloxlink-premium)
* [Magic Roles](#magic-roles)
* [Virtual Groups](#virtual-groups)
* [Cool things you can do with Bloxlink](#cool-things-you-can-do-with-bloxlink)
* [Frequently Asked Questions](#frequently-asked-questions)

### Getting Started
The easiest way to setup Bloxlink is with the `!setup` command.  Check your Direct Messages after using the setup command. <br/>
Note: if you want to skip a setting and leave it as what it was before (or to its default value), say `skip` or `next`. <br/>
The command will walk you through the following steps:
* _Would you like to link a ROBLOX group to this Discord server?_
	* If you want to link your group, specify the group ID here.  Linking your group unlocks group-specific commands, and enables the automatic giving of roles. A member’s rank will also show in the `!getinfo` command.
		* Default: 0 (no group)
* _Would you like to change the Verified role name to something else?_
	* The verified role is the role users get when they link their Roblox account to their Discord account. 
		 Default: Verified
* _Premium informational post_
* _Would you like to automatically transfer your ROBLOX group ranks to Discord roles?_
	* This will create Discord roles that match your Roblox group (if you’ve provided a group id previously).
		* Options: merge, replace
			* Merge: NO Discord roles will be deleted. Group roles will be added right under your roles already there.
			* Replace: ALL Discord roles will be DELETED and REPLACED with the new group roles.
		* Default: none (nothing will change to the roles)
* _Would you like to set a nickname for new members that join your server?_
	* This will set a nickname for each member that joins the server. Refer to the [Nickname Templates](#nickname-templates) section for more information.
### Nickname Templates
The nickname template is a set of instructions that determines what nickname a person gets if they use a command that gives nicknames. In addition, if certain server features are enabled, the nickname will be applied when the person joins the server.
You *CANNOT* omit the {} for the templates.
The templates are:
```
{roblox-name} --> changes to their ROBLOX Username
{discord-name} --> changes to their Discord username
{discord-nick} --> used to reflect no nickname template if this is the only template
{roblox-id} --> changes to their ROBLOX ID
{group-rank} --> changes to their current rank in the linked group
{group-rank-id} --> replace id with your group ID. The person will get the group rank corresponding with the group id. Example: {group-rank-1337}
{clan-tag} --> allows the user to specify a clan-tag with !clantag
```
You can use multiple. For example: `{roblox-name} | {group-rank}` will output: `robloxian123 | HR` if their group rank is “HR”. Note: for `{group-rank}`, the group is taken directly from the “Main Group” (!setup).
*If you would like a user be allowed to change part of their nickname at will*, use the *{clan-tag}* nickname template; otherwise, their nickname will be reverted while using the normal functionality of the bot
If you want to have *no nickname template*, USE `{disable-nicknaming}`, as this will not apply a nickname to the user.
<br/>
<br/>
NOTE: there is a **max of 32 characters** that can be used for nicknames due to Discord limitations. Bloxlink will take the first 32 characters and use that for the nickname.
### Group Roles
There are 2 ways to tell Bloxlink to give your members roles.
#### Main Group:
This is probably the easiest way to deliver group roles. If your group is linked via !setup, *and* there is a Discord role in your server that matches the member’s Group Roleset, then the user will get the role. Please note: roles will *only* be automatically created if done by !setup. There is a `!dynamicroles` command which will make group roles that are missing from the Discord server. By default, this is turned on.
#### Binds:
Note: binds are more advanced, but offer more freedom for specifying who gets what role. <br/>
To make a bind, use `!bind`. The command will ask for your Roblox Group ID, the name of a Discord role in your server, and a list of Roblox Group Rolesets that will get the role. You can call the command to get into the prompts (the bot will ask for the values), or you can do it with one go:
`!bind 123 | My Awesome Role | 1, 3, 5-10` <br/>
Take note of the last value.  Those numbers are Roleset IDs. Bind values MUST 100% MATCH the member’s roleset for that group for them to get the role. Example: a value of `1` will match everyone in that group with a roleset of `1`, not higher or lower. To account for a larger range, negate the number. Example: `-10` means everyone with Roleset 10 *and higher*. You can also specify a range: `1-3` means Rolesets `1, 2, 3`. Please note that there is a max on the amount of binds you can do. If you want to bind all ranks, then just use `!setup`, as that’s the easiest way to link your group. Binds are for when you want *verify specific* ranks to get a certain role.
<br/>
<br/>
Note: another way to do binds is with Virtual Groups. See [Virtual Groups](#virtual-groups) for more information.
### Permissions
Most administrative commands require the `Manage Server` permission. To grant a user the permission, make a new Discord role, and check `Manage Server`. Give it to the person; they will now be able to use administrative Bloxlink commands, such as the `!settings` command. <br/>
Some commands require other permissions than Manage Server, though. Those commands will specify which permission the person needs to run it. <br/>
<br/>
Note: it is possible to override this behavior with Magic Roles. See the [Magic Roles](#magic-roles) section for more information.
### Power Ups
By default, Bloxlink doesn’t do much. Sure, you can use `!setup` and link your group, but what if you want Bloxlink to do things automatically? <br/>
*Power Ups* allow Bloxlink to verify users automatically, and do other actions.
Power ups must be activated by command toggles. <br/>
Current Power Ups:
* !autoverify
	* Bloxlink will give the Verified role and update the member’s nickname on join, if they apply to the person.
* !dynamicroles
	* Bloxlink will attempt to create missing group roles from your server. Note: this will create roles from the “Main Group” only, not from binds.
* !autoroles
	* Bloxlink will give _all_ roles and binds that apply to the person on join. This is different from `!autoverify` that only gives the verified role and nickname. This is equivalent to the user manually running `!getrole`.
* !persistroles (premium)
	* Bloxlink will update roles and nickname when a user starts typing, no command needed from them! This is very useful if you want to ensure active members in your server are always up-to-date in terms of roles and nicknames.
* !grouplock (premium)
	* Bloxlink will kick anyone not in the Main Group. This is used if you want only group members to join your server. Before kicking the person, Bloxlink will DM them with the instructions on verifying and joining the group.
### Command Usage
To view the commands, use `!help`. The bot will list the usage for each command. Certain commands are based off *prompts*— aka the bot will ask you what argument you want to use for the command. Most of these prompts can be skipped with the pipe ` | ` character to aid in command efficiency. 
Example: `!somecommand arg1 | this is another arg | last arg here`
### Bloxlink Premium
Bloxlink premium allows you to supercharge your Bloxlink experience and efficiently manage your Roblox server members.
To see what premium offers, use the `!help` command and skip to the Premium category. 
You can buy premium a few ways:
*  [Selly](https://selly.gg/u/bloxlink)
*  [Patreon](https://patreon.com/bloxlink)

<br/>

If you purchase premium from Selly, you’ll get a code delivered to your email. Redeem the code with `!redeem <code>` in a server you own. <br/>
If you purchase from Patreon, link Discord account to your Patreon account from your Patreon settings page. After this, you will automatically receive Bloxlink premium after 5 minutes.
### Magic Roles
Magic roles are ways to bypass certain Bloxlink restrictions. To create a Magic Role, create a new Discord role with the exact name as below, then give it to a person. <br/>
<br/>
The magic roles are as follows:
*  Bloxlink Bypass
	* Bloxlink will NOT update roles and nicknames for people with these roles.
* Bloxlink Updater
	* Users with this role can run *!updateuser* on other people, as well as run *!verifyall*
* Bloxlink Admin
	* Users with this role can use *any* Bloxlink command.
### Virtual Groups
Virtual groups are another way of doing binds. Basically, virtual groups are binds for anything not group related. For example, you can bind a role for people that own an asset (gamepass, badge, etc.). <br/>
To create a new virtual group, use the corresponding command:
*  !assetbind
	*  Use this to bind a role for people that own an asset. Just provide the ID of the asset (found in the URL - it should just be numbers)
*  !devforumbind
	*  Use this to bind a role for people that are devforum members.
*  !premiumbind
	*  Use this to bind a role for people that have Bloxlink premium.
To delete a virtual group, just use the `!delbind` command. To view all binds, use `!viewbinds`.
### Cool things you can do with Bloxlink
*  Ever wanted to have Bloxlink relay group shouts to your Discord channel? You can with the `!shoutproxy` command! This is a premium command
*  Clan tags! Put {clan-tag} in the nickname template, and users can assign text there with `!clantag <text>`.
*  Link multiple accounts! Use `!verify -add` to add a new user to your Discord account, then use `!switchuser` on another server to verify as that user.
*  [Power-Ups](#power-ups) are pretty cool too...
### Frequently Asked Questions
*  Why isn't Bloxlink responding to me?
	*  Most like, your prefix is messed up. Use `@Bloxlink prefix` and take note of your prefix. You use this prefix for all bot commands. If you see that your prefix is messed up, you can change it with the `@Bloxlink setprefix` command.
	*  If this is not the case, then likely Bloxlink is down either due to planned outage for updates, or Discord is having problems. Keep track of the announcements channel over at the [Bloxlink Discord server](https://discord.gg/g4Z2Pbx) for more information.
*  How do I setup Bloxlink?
	*  Simple! You can setup your server by saying !setup. From there, you can link your group, add the group roles to your server, etc. After your server is linked, !getrole will be activated. If you want to setup group binds, you can from the !bind command. For more information on binds, see [binds](#binds)
*  How can Bloxlink remove old roles?
	*  If a person has a role from the main linked group, but the role doesn't apply to them, the role will be removed. If using binds, the bind can no longer apply to the user for the role to be removed. For example, if your bind is for rank ``1``, once a person reaches rank ``2``, the role for rank 1 will be removed. If you have negated ranks (ranks that capture everyone with that rank and above), then a person has to be below that rank for the role to be removed, same thing with ``all``.
	*  Now, **if you don't want Bloxlink to remove old roles**, do this: `!settings change allowOldRoles true`
*  I don't see a Bloxlink role!
	*  That means you didn't add the bot via the original OAuth link, or you unchecked all permissions. You can make a role for Bloxlink and give it to the bot. Make sure to give the role the appropriate permissions, and **drag** the role above the other roles. If you're not sure what permissions to give, then just give it Administrator.
*  What is Bloxlink Pro, and how do I get it?
	*  Bloxlink Pro is a private version of Bloxlink that only premium users can use. It's on less servers, so it's therefore more reliable than the public version. If you have Bloxlink premium, then you can add the bot via: <https://blox.link/pro>. Note: **If the pro and main bots are both in a server, then Pro's prefix will be ``!`` (or the custom prefix), while the public bot will have a prefix of ``!!``**
*  How do I unlink an account?
	*  Since you can have multiple accounts linked with Bloxlink, you can change your account with `!verify -add`, then use `!switchuser` on all servers you're in with Bloxlink.
*  I don't want Bloxlink to nickname users!
	*  Set a nickname template of `{disable-nicknaming}` to disable nicknaming via: `!settings change nicknameTemplate {disable-nicknaming}`
*  How can I disable Bloxlink from DMing users that join my server?
	*  Use: `!joindm disable`
*  Who made Bloxlink?
	*  Bloxlink was created and is currently developed by one person: justin#1337 on Discord. I am not taking any other developers.
