# caddy-l4

Публичный образ Caddy с модулем [`mholt/caddy-l4`](https://github.com/mholt/caddy-l4)
для установщика [multitool](https://github.com/chess98/multitool).

```text
ghcr.io/chess98/caddy-l4:2.11.7-l4.0.1.2
```

В образе только Caddy, плагин layer4 и стандартные CA-сертификаты. Никаких
токенов, ключей и конфигов ноды нет — образ безопасно публиковать.

## Теги

`<версия Caddy>-l4.<версия плагина>`, например `2.11.7-l4.0.1.2`.
Теги неизменяемые; обновление — новый коммит/тег.

## Сборка

```bash
docker build -t caddy-l4:2.11.7-l4.0.1.2 \
  --build-arg CADDY_VERSION=2.11.7 \
  --build-arg CADDY_L4_VERSION=v0.1.2 caddy-l4
docker run --rm caddy-l4:2.11.7-l4.0.1.2 caddy list-modules | grep -qx layer4
```

CI: GitHub Actions собирает и публикует образ в GHCR при пуше в `main`,
по тегу `v*`, по расписанию (еженедельно) и вручную.
