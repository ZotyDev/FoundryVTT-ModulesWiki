<a href="https://foundryvtt.com/packages/object-interaction-fx">
    <p align="center">
        <img src="https://raw.githubusercontent.com/wiki/ZotyDev/objects-interactions-fx/images/title.png" alt="Automated Objects, Interactions and Effects">
    </p>
</a>

_**[Source](https://github.com/ZotyDev/objects-interactions-fx)**_

_⚠️ W.I.P ⚠️ - Information here may be incomplete_

**If you are facing problems or something is not working as it should, make sure:**
- Tags are written **exactly** like the master tags (they are case sensitive and spaces are included)
- The feature that that you want to use is enabled
- You are using the right tags
- The tags you are using are enabled on Master Tag Settings
- Check if there are updates for the modules (don't worry, Tag data structure is and always will be simple, you can just rollback and things will work again)
- If you are still having problems, please make a [Issue](https://github.com/ZotyDev/objects-interactions-fx/issues/new?assignees=ZotyDev&labels=bug%2Ctriage&projects=&template=BUG_REPORT.yml&title=%5BBUG%5D%3A+)

Do you have questions about the functionalities? Feel free to ask me anything on [Discord](https://discord.gg/RAgPXB4zG7)

## Master Tags
OIF utilizes **Tags** (from [🏷️ItemTags](./../itemTags/introduction.md)) and **Master Tags**, the former can be inserted at any item and will be utilized when needed to determine what sort of automations, interactions or effects are going to be executed, also how they will happen. The last is where the fun begins, **Master Tags** are defined by the user and can be customized at will, allowing you to fine tune the effects.

> [Here](./customization.md) you can learn to create and customize Master Tags

## Tag Packs
You can create collections of **[Master Tags](#master-tags)**, these collections are arranged in **Tag Packs**, that you can export and swap at any time, including while your game is still running.

_imagine chaning the animation of all weapons in the middle of the game, the possibilites..._

## Default Packs
There are default packs containing predefined tags if you don't want to do the boring stuff, you can also export and import tag packs. Note that the packs are **globally available**, you can access the same pack on every world.

The current default packs are:
- [Empty](https://github.com/ZotyDev/objects-interactions-fx/blob/main/data/defaultTagPacks/Empty.json) _used as reference for creating new [tag packs](#tag-packs)_
- [Fantasy (JB2A Complete)](https://github.com/ZotyDev/objects-interactions-fx/blob/main/data/defaultTagPacks/FantasyJB2AComplete.json)
- [Fantasy (JB2A Free)](https://github.com/ZotyDev/objects-interactions-fx/blob/main/data/defaultTagPacks/FantasyJB2AFree.json)
- [Fantasy (No Animations)](https://github.com/ZotyDev/objects-interactions-fx/blob/main/data/defaultTagPacks/FantasyNoAnimations.json) _if you just want to use the interactions and automations_
