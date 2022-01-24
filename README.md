# Pycord-Paginator

This is a paginator for pycord.
It takes a list of embeds and makes them paginated with buttons

![Example](https://github.com/FusionSid/Pycord-Paginator/blob/main/example.png)

## Usage

```
from paginator import Paginator

async def func_name(ctx):
    embed1 = discord.Embed(title="Click the arrows", description="To look through the embeds")
    embed2 = discord.Embed(title="Test", description="Lol")
    embed3 = discord.Embed(title="Test", description="Lol")

    ems = [embed1, embed2, embed3]

    view = Paginator(ctx=ctx, ems=ems)

    message = await ctx.send(embed=embed1, view=view)

    # This part is optional but it makes it so that once the button timeouts it will be disabled so you wont get any INTERACTION FAILED errors.
    res = await view.wait()
    if res:
        for i in view.children:
            i.disabled = True
    return await message.edit(view=view)

```
