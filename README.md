# HPET

![logo](https://i.imgur.com/ViZiV7i.png)

## How to configure HPET?

First of all, you should have 3 files, config.yml, messages.yml, pets.yml
You can change general settings from config.yml, also notice that /pet reload command sometimes could not reload this file
You can configure plugin messages from the messages.yml file, you can translate every message in your language, or just make the messages look better, if you have troubles with YAML files I recommend using a YAML parser, here it is one https://codebeautify.org/yaml-parser-online
You can setup your own pets or edit the existing ones in pets.yml file, everything about the pet is written there

## How to configure pet skins

### Default
You can use Base64 codes for pet skins, you can find them on https://minecraft-heads.com, else you can use player names as valid pet skins, the plugin will automatically detect the right mode, you can find player names on https://namemc.com

### How do I use CustomModelData models?
Use (material): followed by the CustomModelData code you want to use, example: "DIAMOND_HOE:3"
You can find a list of valid materials on https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html

### How do I use ModelEngine?
Use MODELENGINE: followed by the model code into the skin value you want, example:
"MODELENGINE:exampleModel"

### How do I use HeadDatabase?
Use HDB: followed by the head code into the skin value you want, example:
"HDB:12345"

## How do I hook into HPET API?

You can download the PetAPI.jar file here on GitHub, add it to your classpath, then add HPET it into your plugin.yml as dependency
> softdepend: Pet

Get the HPET API:
> Pet.getApi();

Example code:
> if(command.getName().equalsIgnoreCase("petrating")) {
>
>   if(!Pet.getApi().hasUserPet(player)) {
>       return false;
>   }
>   UserPet pet = Pet.getApi().getUserPet(player);
>   if(pet.getType().getName().equals("ghast")) {
>       player.sendMessage("Hey! Your pet is really cool!");
>   } else {
>       player.sendMessage("Your pet is not cool!");
>   }
>   return true;
> }
>
> @EventHandler
> void onPetSelect(PetSelectEvent event) {
>   event.getPlayer().sendMessage("Hello world!");
> }
