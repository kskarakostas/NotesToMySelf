
# Python Snippets

## Generic imports

```python
!/usr/bin/python3 -m pip install --upgrade pip
!pip install -U pandas sklearn transformers nltk

import nltk
nltk.download('stopwords')
nltk.download('wordnet')
```

## Suppress TF2 warnings

```python
import logging, os

logging.disable(logging.WARNING)
os.environ["TF_CPP_MIN_LOG_LEVEL"] = "3"
```

## Print CUDA & GPU info

```python

def PrintGPUInfo(via_torch=True, via_nvcc=True, via_nvidia_smi=True, via_nvidia_smi_lite=True):
    n_spacers = 34
    import subprocess
    if via_torch:
        import torch
        device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
        hdr = f"{'='*n_spacers} torch {'='*n_spacers}"
        print(hdr)
        print(f"Device to be used: {device}")
        if device.type == 'cuda':
            print(f"Total GPUs: {torch.cuda.device_count()}")
            gpu_id = torch.cuda.current_device()
            print(f"Now using : {torch.cuda.get_device_name(gpu_id)} with id: {gpu_id}")
            print('Memory Usage:')
            print(f'Allocated: {round(torch.cuda.memory_allocated(gpu_id)/1024**3,1):6.1} GB')
            print(f'Cached: {round(torch.cuda.memory_reserved(gpu_id)/1024**3,1):6.1} GB')
        print('='*len(hdr), '\n\n')

    if via_nvcc:
        result = subprocess.run(['nvcc', '--version'], stdout=subprocess.PIPE)
        hdr = f"{'='*n_spacers} nvcc {'='*n_spacers}"
        print(hdr)
        print(result.stdout.decode('utf-8').strip())
        print('='*len(hdr), '\n\n')

    if via_nvidia_smi or via_nvidia_smi_lite:
        hdr = f"{'='*n_spacers} via_nvidia {'='*n_spacers}"
        print(hdr)
        result = subprocess.run(['nvidia-smi'], stdout=subprocess.PIPE)
        gpu_info = result.stdout.decode('utf-8').strip()
        if gpu_info.find('failed') >= 0:
            print('Select the Runtime > "Change runtime type" menu to enable a GPU accelerator, ')
            print('and then re-execute this cell.')
        else:
            if via_nvidia_smi:
                print(gpu_info, '\n\n')
            if via_nvidia_smi_lite:
                print('\n'.join(gpu_info.split('\n')[:4]))
        print('='*len(hdr), '\n\n')


```
