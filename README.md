import discord
import random, os
import requests

from discord.ext import commands
intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='!', intents=intents)

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.command()
async def hola(ctx):
    await ctx.send(f'Hola, soy {bot.user} soy el bot de mi dueño!')

@bot.command()
async def animal(ctx):
    await ctx.send('hola soy un animal!')

@bot.command()
async def  botsaludaajuanda(ctx):
    await ctx.send(f'hola juanda soy {bot.user}!')

@bot.command()
async def mem(ctx):
    # ¡Vamos a elegir una imagen al azar de la carpeta "images"!
    img_name = random.choice(os.listdir('images'))
    with open(f'images/{img_name}', 'rb') as f:
        # ¡Vamos a almacenar el archivo de la biblioteca Discord convertido en esta variable!
        picture = discord.File(f)
    # A continuación, podemos enviar este archivo como parámetro.
    await ctx.send(file=picture)
bot.run('your_token_here')
