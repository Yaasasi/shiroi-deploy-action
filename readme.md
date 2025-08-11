# Shiroi Deploy Workflow

GitHub Action 构建 Shiroi 工作流

## Secrets

- `GH_PAT` 可访问 Shiroi 仓库的 Github Token

### Github Token

1. 你的账号可以访问 Shiroi 仓库。
2. 进入 [tokens](https://github.com/settings/tokens) - Personal access tokens - Tokens (classic) - Generate new token - Generate new token (classic) 

![](https://github.com/innei-dev/shiroi-deploy-action/assets/41265413/e55d32cb-bd30-46b7-a603-7d00b3f8a413)

## Deploy

安装 Node.js, npm, pnpm, pm2, sharp。

关于 sharp 的安装，你可以使用

```sh
npm i -g sharp
```

sharp 不是必须的，但是在运行过程中会出现报错。参考：https://nextjs.org/docs/messages/sharp-missing-in-production

在你的服务器家目录，新建 `shiro` 的目录，然后新建 `.env` 填写你的变量。

```
# Env from https://github.com/innei-dev/Shiroi/blob/main/.env.template
NEXT_PUBLIC_API_URL=
NEXT_PUBLIC_GATEWAY_URL=

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=

## Clerk
CLERK_SECRET_KEY=

NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/

TMDB_API_KEY=

GH_TOKEN=
```

## Tips

为了让 PM2 在服务器重启之后能够还原进程。可以使用：

```sh
pm2 startup
pm2 save
```
