# BayesianMethods.jl
My take on learn about Probabilistic Programming with [Turing.jl](https://turing.ml/dev/) by implementing the book [Probabilistic Programming & Bayesian Methods for Hackers](https://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/).

# Usage
Recommended: Install the vscode [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) plugin and load the [devcontainer](https://code.visualstudio.com/docs/remote/containers).
Alternatively install julia locally, activate and instantia the `BayesianMethods` environment.

# Debug in vscode
The vscode julia debugger crashes when loading the native OpenGL functions.
Enabling the **Compiled Mode** as described [here](https://www.julia-vscode.org/docs/stable/userguide/debugging/) seems to be a workaround.

# IJupyter
Based on Jupyter, IJupyter can be used for explorative coding.
To use IJupyter, you have two choices:
- Create a *.ipynb* file and open it in vscode.
  The Jupyter extension will automatically launch the Jupyter server.
- Launch `jupyter lab --allow-root` from an integrated terminal.
  Hold Alt + Click the link to open the notebook.