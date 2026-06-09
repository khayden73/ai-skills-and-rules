# My personal Skills and Rules for AI tools

LOL, just realized that rhymes. I'm a poet and didn't know it. 

## Tools

As of right now, I'm mostly just using Claude so these skills were created for and used with Claude Code.
They may or may not work with other agents, Feel free to download and try them out.

## What's Here

### Skills

Several Skills I've created and used in my projects, including:
- Changelog generator
- Pull Request summary generator
- Todo list
- Feature List
- Issue Tracker - allows you to add, and change status of, issues

I've been using the issue tracker extensively lately as I am building out a desktop app using ElectronJS and as I do my own QA, I notice issues and have Claude add them to a list by priority and tag.
Then as I knock items off the list I update them.

For every PR I create, I add a Changelog entry that bumps the minor or patch version. Major version will get bumped when I release final product.

Both the changelog and pull request summary generator will do a diff on your current branch to create a list of things that changed.

## Usage

Documentation coming soon...
### Issue Tracker

```shell
/issue-tracker add <description> [-p priority] [-t tag]   Add a new issue (prompts for missing priority/tag)
/issue-tracker list [status] [priority] [tag]             List issues, optionally filtered
/issue-tracker start <number|partial>                     Mark an issue in progress
/issue-tracker fixed <number|partial>                     Mark an issue closed — fixed
/issue-tracker wontfix <number|partial>                   Mark an issue closed — won't fix
/issue-tracker remove <number|partial>                    Delete an issue entirely (confirms first)

```


### Rules

Some of my goto rules for the agent when I build React apps. There's rules in there for HTML, CSS and Accessibility as well.

I need to rework some of the rules a bit as they were built for a specific project and need to be more generic.

## Contributing

I welcome contributions and PRs if you have ideas on improvements.

## License

Use it as you like. Attribution is appreciated but not enforced.

## Check out these other cool things
- [This Old Dev](https://thisold.dev) - a personal look back at all the technologies I've used in my career
- [My Developer Blog](https://keithhayden.dev) - My personal Developer Blog, built with NextJS and MDX
- [ninthplanet.software](https://ninthplanet.software) - My consulting business
- My friend Daniel Hayes Smith created a starter [AI folder template](https://github.com/danielhayessmith/ai-folder-template) that you might find useful
- Another friend, also named Dan, has some merch on his [Master Time Waster site](https://mastertimewaster.com/)

## Keep me caffeinated

If you feel so inclined, you could help [support my latte habit](https://buymeacoffee.com/KHaydenWebDev)

