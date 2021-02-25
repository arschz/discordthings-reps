# Menciones
¿Tratando de remover las menciones? Aquí hay algunos ejemplos de lo que debe usar.

*Nota: asegúrese de que está viendo el ejemplo de su biblioteca y tiene instalada la versión de biblioteca requerida o superior, de lo contrario no funcionará.*

## Discord.py (requires v1.4.0 or higher)

Hay múltiples opciones: 
1) Agrega `, allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False)` después de la salida de su comando (Funciona solo para mensajes individuales).
2) Ponlo en tu cliente (Si hace esto, todos los mensajes que envíe su bot no harán ping a nadie de forma predeterminada).

**╠ Ejemplo 1**Si no está subclasificado (allowed_mentions = discord.AllowedMentions(roles=False, users=False, everyone=False),):
```py
class Bot(commands.AutoShardedBot):
    def __init__(self, **kwargs):
        super().__init__(
            allowed_mentions = discord.AllowedMentions(roles=False, users=False, everyone=False),
        )
```

**╚ Ejemplo 2** Si no está subclasificado (allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False))):
```py
bot = commands.Bot(allowed_mentions=discord.AllowedMentions(roles=False, users=False, everyone=False))
```

## Discord.JS (requires v12.2.0 or higher)

Hay múltiples opciones:
1) Agrega `, {allowedMentions: {parse: []}}` después de la salida de su comando (Funciona solo para mensajes individuales).
2) Ponlo en el cliente. (Si hace esto, todos los mensajes que envíe su bot no harán ping a nadie de forma predeterminada).

**╚ Ejemplo** [[src]](https://github.com/discordextremelist/website/blob/5394fcd179d5fc75e0ef9fbb9e674186a13f620a/src/Util/Services/discord.ts#L30)
```js
const client = new Discord.Client({
    allowedMentions: { parse: [] }
});
```

## Eris (requires 0.12.0 or higher)

Actualmente solo hay una opción conocida. Si esto no funciona, consulte el [Eris documentation](https://abal.moe/Eris/docs/PrivateChannel#function-createMessage).

**╚ Ejemplo** Agregue esto a sus opciones de Eris [[src]](# "Franklin#8888 (425966117840748545)")
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
1. Establecer las menciones predeterminadas que se utilizarán para cada MessageAction con `MessageAction.setDefaultMentions(Collection<Message.MentionType>)`, que luego se puede anular con la siguiente opción
2. Anexando `.allowedMentions(Collection<Message.MentionType>)` después de una MessageAction

**╠ Ejemplo 1** En tu método principal, por ejemplo
```java
EnumSet<Message.MentionType> disabled = EnumSet.of(Message.MentionType.EVERYONE, Message.MentionType.ROLE);
EnumSet<Message.MentionType> mentions = EnumSet.complementOf(disabled); // all mentions except everyone and roles
MessageAction.setDefaultMentions(mentions);
```

**╠ Ejemplo 2** After a MessageAction
```java
EnumSet<Message.MentionType> mentions = EnumSet.of(Message.MentionType.USER); // only user mentions
channel.sendMessage(...).allowedMentions(mentions).queue();
```

## Discord.NET (requires 2.3.0 or higher)

**╚ Ejemplo** para un solo mensaje:
```csharp
await ReplyAsync(..., allowedMentions: AllowedMentions.None)
```
