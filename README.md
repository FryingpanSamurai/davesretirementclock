# Dave's Retirement Clock

Dave is coming up on his retirement date.
So, I thought it would be fun to do a little project to implement a CI/CD stream
using Azure Static Web Apps.

Auto-generated domain name provided by azurestaticapps.
*Maybe we'll get a domain?*

## Development
This was developed using Svelte and SvelteKit.
It could have been built using only svelte, in that: I did not need to query any API's or DB's over the backend. 

## Research and Implementation
I'm new to the CI/CD scene, so I thought it would be appropriate to start close enough to a zero-config environment. I've used VM's through Azure in the past, so I thought I'd give azure static web apps a shot. I do enjoy the way you can easily deploy your application from the Github source repository and seemlessly push any updates from repo to live production.

## Considerations
I would be remiss if I did not do my due diligence in completing this lab.
And so, future projects will include adopting alternative options to implementing a CI/CD chain. 

## Future
Other labs will include:
- on-prem CI/CD exercises inside and outside a windows domain.
- Linux CI/CD deployment options
- VM CI/CD deployment options via Cloud Computing (PaaS/IaaS)
- Alternative options to azure like Jenkins (using containers), TeamCity, Bamboo