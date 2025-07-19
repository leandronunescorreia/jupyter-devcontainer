## How configure devcontainer?

### first create the base image based on nvidia distro

```bash
docker build --no-cache -t ubuntu22-cuda118-py310-pt251 -f .devcontainer/Dockerfile.base .
```

If you run the container manually:

```bash
docker run --rm --gpus all -it ubuntu22-cuda118-py310-pt251 bash
```

Inside the container, test with:

```bash
python3 -c "import torch; print(torch.cuda.is_available())"
```

```bash
nvcc --version
```

```bash
nvidia-smi
```

After create this base image and test if GPU is enabled, open Command Palette (`Ctrl+Shift+P`), select **"Dev Containers: Reopen in Container"**.

VS Code will build the container using `.devcontainer/dev.Dockerfile` (see the "create the base image first" section below) and set up the environment automatically.

You can customize the dev container by editing `.devcontainer/devcontainer.json` and related files.


