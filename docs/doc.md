# documentation

## private notes on setup
https://docs.google.com/document/d/1fy6fBrFXDZjmHlJwLRKq_i4bd4X89bT0F6n8un4c9ro/edit?usp=sharing

As detailed in the above gdoc, I installed the relevant AWS IDE for PyCharm and confirmed it worked.

The "secrets" folder of this project will only store files locally (_i.e._ not in git). 
Certain configuration files for AWS integration are in the virtual environment associated with this PyCharm project, and those are also local.

When it doesn't make sense to track files created here in git (e.g., a ~300 MB cdk demo), these will be added to .gitignore.