# Menciones
¿Tratando de remover las menciones? Aquí hay algunos ejemplos de lo que debe usar.

*Nota: asegúrese de que está viendo el ejemplo de su biblioteca y tiene instalada la versión de biblioteca requerida o superior, de lo contrario no funcionará.*

## Discord.py (requires v1.4.0 or higher)

Hay múltiples opciones: 
1) Add `, allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False)` after the output of your command. (Works for individual messages only).
2) Put it into your client. (If you do this, all messages your bot sends will ping nobody by default).

**╠ Example 1** If you have it subclassed [[src]](https://github.com/TheMoksej/Dredd/blob/76ff9608af1bd5a09a89f523996d57103a83b471/bot.py#L107):
```py
class Bot(commands.AutoShardedBot):
    def __init__(self, **kwargs):
        super().__init__(
            allowed_mentions = discord.AllowedMentions(roles=False, users=False, everyone=False),
        )
```

**╚ Example 2** If it's not subclassed [[src]](https://github.com/discordextremelist/bot/blob/915d203ca2b4ae4bbf9f55cb303c5dc5a4b17e8f/bot.py#L59):
```py
bot = commands.Bot(allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False))
```

## Discord.JS (requires v12.2.0 or higher)

Hay múltiples opciones:
1) Add `, {allowedMentions: {parse: []}}` after the output of your command. (Works for individual messages only).
2) Put it into the client. (If you do this, all messages your bot sends will ping nobody by default).

**╚ Example** [[src]](https://github.com/discordextremelist/website/blob/5394fcd179d5fc75e0ef9fbb9e674186a13f620a/src/Util/Services/discord.ts#L30)
```js
const client = new Discord.Client({
    allowedMentions: { parse: [] }
});
```

## Eris (requires 0.12.0 or higher)

There is currently only one known option. If this does not work please refer yourself to the [Eris documentation](https://abal.moe/Eris/docs/PrivateChannel#function-createMessage).

**╚ Example** Add this to your Eris options. [[src]](# "Franklin#8888 (425966117840748545)")
```js
{
  allowedMentions: {
    roles: false,
    everyone: false
  }
}
```

## JDA (requires 4.2.0 or higher)

Hay múltiples opciones:
1. Setting the default mentions that will be used for each MessageAction with `MessageAction.setDefaultMentions(Collection<Message.MentionType>)`, which can then be overriden with the next option
2. Appending `.allowedMentions(Collection<Message.MentionType>)` after a MessageAction

**╠ Example 1** In your main method for example
```java
EnumSet<Message.MentionType> disabled = EnumSet.of(Message.MentionType.EVERYONE, Message.MentionType.ROLE);
EnumSet<Message.MentionType> mentions = EnumSet.complementOf(disabled); // all mentions except everyone and roles
MessageAction.setDefaultMentions(mentions);
```

**╠ Example 2** After a MessageAction
```java
EnumSet<Message.MentionType> mentions = EnumSet.of(Message.MentionType.USER); // only user mentions
channel.sendMessage(...).allowedMentions(mentions).queue();
```

## Discord.NET (requires 2.3.0 or higher)

**╚ Example** for a single message:
```csharp
await ReplyAsync(..., allowedMentions: AllowedMentions.None)
```
