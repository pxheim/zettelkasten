Working with a PR pattern while also doing CI/CD can be difficult. The very nature of waiting for someone to review your PR is antithetical to continuously integrating your changes. To get around this, we will employ the "ship / show / ask" strategy, which in simple terms mean that each every change you make is will fall under one of these categories.

# Ship - Commit directly to main

This tag is for the smallest of changes where no review is required. Things like minor fixes, language changes, typos, etc. fall under this category. When making these changes you can commit them directly to the main branch.

# Show - PR without review

The most common tag for any changes larger than just a few lines. Make a PR with your changes, but do not wait for any review (you'll still wait for checks to pass). This is done so that you can people can review your changes _after_ the fact to see what you did.

# Ask - PR with review

For larger changes or when you are not sure whether the changes you are making is a good fit or not. Here you make a PR and wait for someone to review it _before_ you merge it.