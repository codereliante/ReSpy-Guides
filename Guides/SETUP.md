<div align="center">
    <img src="https://cdn.discordapp.com/icons/1032763361806536805/7475550d0be2cd987ad6c0c0555005ec.webp?size=56" height="200" width="200">
    <h2>ReSpy</h2>
    <p align="center">
	<p>ReSpy — a paid seamless Discord utility bot.</p>
        </a> </p>
    </p>
</div>

# ReSpy Documentation
## Contents
* [Getting Started](#getting-started)
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
