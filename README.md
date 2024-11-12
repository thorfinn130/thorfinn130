import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix="!", intents=intents)

# ბოტის გაშვებისას ინფორმაცია
@bot.event
async def on_ready():
    print(f'ბოტი ჩართულია, სახელით: {bot.user}')

# მესიჯის პასუხი კონკრეტულ ფრაზაზე
@bot.event
async def on_message(message):
    if message.author == bot.user:
        return

    # ქართული და ინგლისური მესიჯების შემოწმება და პასუხი
    if message.content.lower() == "thorfina ravaxar":
        await message.channel.send("ravi aramishavs")
    elif message.content.lower() == "ტორფინა რავახარ":
        await message.channel.send("რავი არაფერს")

    # თუ სხვა კომანდები გაქვთ, საჭიროა ეს კოდი შეტყობინებების პროცესინგის დასასრულებლად 
    await bot.process_commands(message)

# ბოტის ტოკენი
bot.run("MTI5NjEyMDg3MzIzMjYyOTg4Mg.GHvZXt.oxXHWT6SeNd67blZKfd1SuRbEaCsEiHKiCGImQ")
