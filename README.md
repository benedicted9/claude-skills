# claude-skills

Marketplace de plugins [Claude Code](https://claude.com/claude-code) qui versionne mes skills perso. Le plugin `mes-skills` regroupe toutes les skills.

## Installation sur une autre machine

Dans Claude Code :

```
/plugin marketplace add benedicted9/claude-skills
/plugin install mes-skills@claude-skills
```

Le repo est privé : `gh auth login` (ou un identifiant Git configuré) doit être fait sur la machine.

## Ajouter une nouvelle skill

1. Créer `plugins/mes-skills/skills/<nom>/SKILL.md` (nom en kebab-case, identique au dossier, avec un frontmatter `name:` et `description:`).
2. Bumper la `version` dans `plugins/mes-skills/.claude-plugin/plugin.json` **et** dans `.claude-plugin/marketplace.json`.
3. Ajouter la skill au tableau ci-dessous.
4. `git commit` + `git push`.
5. Sur chaque machine : `/plugin marketplace update claude-skills`.

## Skills du plugin

| Skill | Description |
|-------|-------------|
| `exemple-skill` | Skill d'exemple à remplacer. |
