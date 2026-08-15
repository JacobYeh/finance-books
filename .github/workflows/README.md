# finance-books workflows

## sync-to-finance-stack.yml

当 books repo push 时, 自动在 `JacobYeh/finance-stack` 创建 PR 更新 submodule 指针.

### Setup (one-time, in finance-stack repo)

1. 去 https://github.com/JacobYeh/finance-stack/settings/secrets/actions
2. 创建 fine-grained PAT:
   - Repository access: Only `JacobYeh/finance-stack`
   - Permissions: `Contents: Write`, `Pull requests: Write`
3. Secret name: `FINANCE_STACK_PAT`
4. 粘贴 PAT 值

### Flow

```
finance-books push
  → workflow triggers
    → checkout finance-stack with PAT
      → git submodule update --remote books
        → if changed:
          → create branch books/sync-{ts}
          → commit + push
          → open PR via gh CLI
```

### Manual trigger

`Actions` → `Sync books → finance-stack` → `Run workflow`
