# discord.js-migration-guide


```markdown
# Guía de Cambios en Discord.js

Esta guía proporciona ejemplos de cambios clave en diferentes versiones de Discord.js, incluyendo v11, v12, v13 y v14.

## v11 → v12

### Cambio en el Manejo de Promesas:

```javascript
// v11
client.on('message', message => {
  message.channel.send('Hello, world!', (response) => {
    console.log('Message sent:', response);
  });
});

// v12
client.on('message', async message => {
  try {
    const response = await message.channel.send('Hello, world!');
    console.log('Message sent:', response);
  } catch (error) {
    console.error('Error sending message:', error);
  }
});
```

## v12 → v13

### Introducción de Interacciones:

```javascript
// v12
client.on('message', message => {
  if (message.content === '!ping') {
    message.channel.send('Pong!');
  }
});

// v13
client.on('interactionCreate', interaction => {
  if (!interaction.isCommand()) return;
  
  const command = interaction.commandName;
  
  if (command === 'ping') {
    interaction.reply('Pong!');
  }
});
```

## v13 → v14

### Cambio en Datos de Comandos:

```javascript
// v13
const command = {
  name: 'ping',
  type: 'CHAT_INPUT',
  options: [{
    name: 'option',
    description: 'A sample option',
    type: 'STRING',
  }],
};

// v14
const { ApplicationCommandType, ApplicationCommandOptionType } = require('discord.js');

const command = {
  name: 'ping',
  type: ApplicationCommandType.ChatInput,
  options: [{
    name: 'option',
    description: 'A sample option',
    type: ApplicationCommandOptionType.String,
  }],
};
```

### Cambio en Componentes de Mensajes:

```javascript
// v13
const button = new MessageButton()
  .setStyle('PRIMARY')
  .setLabel('Click me')
  .setCustomId('button-click');

// v14
const { ButtonStyle } = require('discord.js');
const button = new ButtonBuilder()
  .setStyle(ButtonStyle.Primary)
  .setLabel('Click me')
  .setCustomId('button-click');
```

## Aviso

Estos son solo ejemplos ilustrativos de los cambios más destacados. Consulta la documentación oficial de Discord.js para obtener información más detallada y actualizada sobre las diferencias entre versiones.
```

Atentamente Rex Dev.
