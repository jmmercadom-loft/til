# Uso de await com .then() - Boas Práticas

## Contexto
O código em questão estáva fazendo uma chamada à API para buscar notificações:

    await api.getNotifications().then(({ items }) => {
      addNewNotifications(items);
    });

## Análise

Usar await junto com .then() geralmente não é considerado uma boa prática por alguns motivos:

1. Redundância
   - O await já espera a Promise ser resolvida
   - O .then() também espera a Promise ser resolvida
   - Estamos essencialmente fazendo a mesma coisa duas vezes

2. Clareza do código
   - Mistura dois estilos diferentes de lidar com código assíncrono
   - Pode confundir outros desenvolvedores que mantêm o código

## Refatoração Recomendada

A forma mais limpa seria usar apenas await:

    const { items } = await api.getNotifications();
    addNewNotifications(items);

Ou apenas .then():

    api.getNotifications().then(({ items }) => {
      addNewNotifications(items);
    });