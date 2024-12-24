FROM adamcoulombe/comfyui-with-flux:latest

# Due to the fact that the models are in a gated repository, we need to download them separately BEFORE building this image and store them locally in a folder called flux
# https://huggingface.co/black-forest-labs/FLUX.1-dev/blob/main/ae.sft
COPY flux/ae.sft /ComfyUI/models/vae/
# https://huggingface.co/black-forest-labs/FLUX.1-dev/blob/main/flux1-dev.sft
COPY flux/flux1-dev.sft /ComfyUI/models/diffusion_models/

# Download and move clip_l.safetensors
RUN wget -O /ComfyUI/models/clip/clip_l.safetensors "https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/clip_l.safetensors?download=true" --progress=bar:force:noscroll

# Download and move t5xxl_fp8_e4m3fn.safetensors
RUN wget -O /ComfyUI/models/clip/t5xxl_fp16.safetensors "https://huggingface.co/comfyanonymous/flux_text_encoders/resolve/main/t5xxl_fp16.safetensors?download=true" --progress=bar:force:noscroll

RUN mkdir -p /ComfyUI/models/controlnet
# Download and move Flux.1-dev-Controlnet-Upscaler.safetensors
RUN wget -O /ComfyUI/models/controlnet/Flux.1-dev-Controlnet-Upscaler.safetensors "https://huggingface.co/jasperai/Flux.1-dev-Controlnet-Upscaler/resolve/main/diffusion_pytorch_model.safetensors?download=true" --progress=bar:force:noscroll

RUN mkdir -p /ComfyUI/models/unet
# Download and move flux1-dev-Q5_0.gguf
RUN wget -O /ComfyUI/models/unet/flux1-dev-Q5_0.gguf "https://huggingface.co/city96/FLUX.1-dev-gguf/resolve/main/flux1-dev-Q5_0.gguf" --progress=bar:force:noscroll

# make the xlabs directory
RUN mkdir -p /ComfyUI/models/xlabs/loras
RUN wget -O /ComfyUI/models/xlabs/loras/Xlabs-AI_flux-RealismLora.safetensors "https://huggingface.co/XLabs-AI/flux-RealismLora/resolve/main/lora.safetensors?download=true" --progress=bar:force:noscroll

CMD [ "/start.sh" ]
