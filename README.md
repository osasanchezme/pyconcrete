# pyconcrete
python module for drawing concrete plan details.

it aims to draw such a beam and columns at the end.

![image](https: // user - images.githubusercontent.com / 8196112 / 55085621 - 97acb100 - 50c4 - 11e9 - 91e6 - 7afcf2d7dbbc.png)

![image](https: // user - images.githubusercontent.com / 8196112 / 55085845 - f70ac100 - 50c4 - 11e9 - 98c4 - 05240751b4d5.png)


It includes BeamType class that itself includes number of Beams class.
at present it can draw beamtype shape, beamsize text, dimension lines and axes lines.

![image](https://user-images.githubusercontent.com/8196112/55087377-a5b00100-50c7-11e9-99cf-55fe3eb8bae2.png)


# Usage

This example show how you can create BeamType and then export that to dxf file
with ezdxf python package for example.
export of this code shown at above.


```python
import ezdxf

from pyconcrete.beamtype import beamtype, beamtypedxf


bt1 = beamtype.BeamType(spans_len=[295, 540],
                        beams_dimension=[(40, 40), (40, 40)],
                        columns_width=dict(
    bot=[45, 45, 40],
    top=[40, 45, 40],),
    stirrups_len=[None, [85, 85]],
    axes_name=[('A', 1), ('B', 1), ('C', 1)],
)


bt2 = beamtype.BeamType(spans_len=[254, 620, 350],
                        beams_dimension=[(40, 40), (40, 45), (40, 50)],
                        columns_width=dict(
    bot=[45, 45, 40, 50],
    top=[40, 45, 40, 45],),
    stirrups_len=[None, [85, 85], [85, 85]],
    axes_name=[('A', 1), ('B', 1), ('C', 1), ('D', 1)],
)

bt3 = beamtype.BeamType(spans_len=[254, 620, 350],
                        beams_dimension=[(40, 40), (40, 30), (40, 40)],
                        columns_width=dict(
    bot=[45, 45, 40, 50],
    top=[40, 45, 40, 45],),
    stirrups_len=[None, [85, 85], [85, 85]],
    axes_name=[('A', 1), ('B', 1), ('C', 1), ('D', 1)],
)

new_dwg = ezdxf.new('AC1024', setup=True)
# btdxf1 = beamtypedxf.BeamTypeDxf(bt1, new_dwg)
# btdxf2 = beamtypedxf.BeamTypeDxf(bt2, new_dwg)
btdxf3 = beamtypedxf.BeamTypeDxf(bt3, new_dwg)
# btdxf1.to_dxf()
# btdxf2.to_dxf()
btdxf3.to_dxf()
msp = new_dwg.modelspace()
# msp.add_blockref(bt1.uid, (100, 150))
# msp.add_blockref(bt2.uid, (100, 0))
msp.add_blockref(bt3.uid, (100, 0))
new_dwg.saveas('/home/ebi/beamtype1.dxf')

```

## output

This is output at peresent, but I add scale parameter and styles to seems look better!

![image](https: // user - images.githubusercontent.com / 8196112 / 55086146 - 8617d900 - 50c5 - 11e9 - 9059 - ee6c569f132d.png)
