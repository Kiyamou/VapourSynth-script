## nnedi3_resample

### Description

* Requirements
  * nnedi3 or znedi3 (faster)
  * nnedi3cl (if `opencl` is `True`)
  * fmtconv
  * mvsfunc

* Usage: Put nnedi3_resample.py into `<python folder>\Lib\site-packages\vapoursynth`

* Function: It can do scaling, color space conversion, etc.

* Note: Internally always processing in 16-bit integer, and the output format can be specified by `csp` with Format id (default is the same as input).

### Usage

```python
def nnedi3_resample(input,
                    
                    # resize
                    target_width=None, target_height=None, 
                    src_left=None, src_top=None, src_width=None, src_height=None,
                    
                    # color formats
                    csp=None, mats=None, matd=None, cplaces=None, cplaced=None,
                    
                    # for Linear - Gamma
                    fulls=None, fulld=None, curves=None, curved=None, sigmoid=None,
                    
                    # function select
                    scale_thr=None,
                    
                    # nnedi3 parameters
                    nsize=None, nns=None, qual=None, etype=None, pscrn=None, opt=None,
                    int16_prescreener=None, int16_predictor=None, exp=None,
                    
                    # fmtc.resample parameters
                    kernel=None, invks=False, taps=None, invkstaps=3,
                    a1=None, a2=None,
                    
                    # fmtc.resample parameters for UV planes
                    chromak_up=None, chromak_up_taps=None,
                    chromak_up_a1=None, chromak_up_a2=None,
                    chromak_down=None, chromak_down_invks=False,
                    chromak_down_invkstaps=3, chromak_down_taps=None,
                    chromak_down_a1=None, chromak_down_a2=None,
                    
                    # opencl=True: nnedi3cl, opencl=False: znedi3 or nnedi3 (if doesn't have libznedi3.dll)
                    opencl=False, device=-1):
```

### Example

Double the width and height of a clip.

```python
import vapoursynth as vs
import nnedi3_resample as nnrs

core = vs.get_core()
    
clip = XXXSource()
clip = nnrs.nnedi3_resample(clip, clip.width * 2, clip.height * 2)

clip.set_output()
```
