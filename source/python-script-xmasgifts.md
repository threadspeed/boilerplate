---
title: python script xmasgifts (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'xmasgifts'

Functions in program: 
* `def msg(player,*text):`
* `def severe(*text):`
* `def info(*text):`

Modules used in program: 
* `import unicodedata`
* `import org.bukkit.event.player.PlayerItemHeldEvent`
* `import org.bukkit.potion.PotionEffectType as PotionEffectType`
* `import org.bukkit.potion.PotionEffect as PotionEffect`
* `import org.bukkit.Bukkit`
* `import org.bukkit.material.MaterialData as MaterialData`
* `import org.bukkit.inventory.ShapedRecipe as ShapedRecipe`
* `import org.bukkit.event.entity.EntityDamageByEntityEvent`
* `import warnings`
* `import java.awt.event.KeyEvent `
* `import random`
* `import org.bukkit.event.entity.EntityDeathEvent`
* `import org.bukkit.event.entity.EntityTargetEvent`
* `import org.bukkit.entity.EntityType`
* `import org.bukkit.entity`
* `import org.bukkit.block`
* `import org.bukkit.plugin.java.JavaPlugin`
* `import org.bukkit.inventory.meta.ItemMeta`
* `import org.bukkit.event.player.PlayerInteractEvent`
* `import org.bukkit.event`
* `import org.bukkit.entity.Player as player`
* `import org.bukkit.command.CommandSender`
* `import org.bukkit.command.Command`
* `import org.bukkit.event.entity.CreatureSpawnEvent`
* `import org.bukkit.inventory.meta`
* `import org.bukkit.inventory.ItemStack as ItemStack`
* `import org.bukkit.event.block.BlockBreakEvent`
* `import org.bukkit.event.Listener`
* `import org.bukkit.event.EventPriority`
* `import org.bukkit.event.EventHandler`
* `import org.bukkit.entity.Player`
* `import org.bukkit.Material`
* `import org.bukkit.enchantments.Enchantment`
* `import org.bukkit.block.Block`
* `import java.util.HashMap`
* `import java.util.ArrayList as ArrayList`
* `import org.bukkit as bukkit`
* `import os,math,re`

## python xmasgifts

Python mysql example: xmasgifts

```python
__plugin_name__ = "XmasGifts"
__plugin_version__ = "1.0"
__plugin_mainclass__ = "brix"

import os,math,re
from java.io import FileInputStream,File
from java.lang import String
from org.bukkit.util import Vector
from org.bukkit.configuration.file import YamlConfiguration
import org.bukkit as bukkit
from java.util.logging import Level
import java.util.ArrayList as ArrayList
import java.util.HashMap
import org.bukkit.block.Block
import org.bukkit.enchantments.Enchantment
import org.bukkit.Material
import org.bukkit.entity.Player
import org.bukkit.event.EventHandler
import org.bukkit.event.EventPriority
import org.bukkit.event.Listener
import org.bukkit.event.block.BlockBreakEvent
import org.bukkit.inventory.ItemStack as ItemStack
import org.bukkit.inventory.meta
import org.bukkit.event.entity.CreatureSpawnEvent
import org.bukkit.command.Command
import org.bukkit.command.CommandSender
import org.bukkit.entity.Player as player
import org.bukkit.event
import org.bukkit.event.player.PlayerInteractEvent
import org.bukkit.inventory.meta.ItemMeta
import org.bukkit.plugin.java.JavaPlugin
Material = bukkit.Material
import org.bukkit.block
import org.bukkit.entity
import org.bukkit.entity.EntityType
log = server.getLogger()
import org.bukkit.event.entity.EntityTargetEvent
from java.util import Random
import org.bukkit.event.entity.EntityDeathEvent
from random import randrange
from random import randint
import random
import java.awt.event.KeyEvent 
import warnings
import org.bukkit.event.entity.EntityDamageByEntityEvent
import org.bukkit.inventory.ShapedRecipe as ShapedRecipe
import org.bukkit.material.MaterialData as MaterialData
import org.bukkit.Bukkit
import org.bukkit.potion.PotionEffect as PotionEffect
import org.bukkit.potion.PotionEffectType as PotionEffectType
import org.bukkit.event.player.PlayerItemHeldEvent
import unicodedata

server = bukkit.Bukkit.getServer()

log = server.getLogger()
CHAT_PREFIX = "[XMAS GIFTS] "
def info(*text):
    log.log(Level.INFO,CHAT_PREFIX+" ".join(map(unicode,text)))
def severe(*text):
    log.log(Level.SEVERE,CHAT_PREFIX+" ".join(map(unicode,text)))
def msg(player,*text):
    player.sendMessage(CHAT_PREFIX+" ".join(map(unicode,text)))

CONSOLE = server.getConsoleSender()


class brix(PythonPlugin):
    def __init__(self):
        PythonPlugin.__init__(self)
        self.api = None
        self.cfg = None
        self.folder = ""
        self.nameChecker = re.compile("^[a-zA-Z0-9\._]+$")
        
    def onEnable(self):
        print("Xmas gifts v1.0 by Brixishuge enabled")
        
    def onDisable(self):
        print("Xmas gifts v1.0 by Brixishuge disabled")
        
    @hook.event("player.PlayerJoinEvent", "HIGHEST")
    def onPlayerJoinEvent(event):
        chance1 = 90
        chance2 = 10
        randomy = random.randint(1, 100)
        randomz = random.randint(1, 100)
        pluginlokacija2 = os.path.realpath("%s/plugins"%os.getcwd())
        if not event.getPlayer().getName() in open("%s/XmasGifts/users.yml"%pluginlokacija2).read():
            try:
                fo = open("%s/XmasGifts/users.yml"%pluginlokacija2, "ab+")
                old = fo.read()
                fo.write("\n- %s"%event.getPlayer().getName())
                event.getPlayer().sendMessage("%sMerry Christmas! Here's a little gift!"%bukkit.ChatColor.RED)
                command = ("eco give %s 350"%(event.getPlayer().getName()))
                org.bukkit.Bukkit.getServer().dispatchCommand(org.bukkit.Bukkit.getServer().getConsoleSender(), command)
                if (randomy <= chance1):
                    command = ("kit xmas %s"%(event.getPlayer().getName()))
                    org.bukkit.Bukkit.getServer().dispatchCommand(org.bukkit.Bukkit.getServer().getConsoleSender(), command)
                else:
                    command = ("kit xmasticket %s"%(event.getPlayer().getName()))
                    org.bukkit.Bukkit.getServer().dispatchCommand(org.bukkit.Bukkit.getServer().getConsoleSender(), command)
            finally:
                fo.close()
        else:
            pass


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
