# for_pa

from pathlib import Path
import os
nas_path = Path(os.environ['NAS_PATH'])

default_template = {
    "pringles": nas_path/"template/pringles/pringles/0",
    "brown_ramen_von_2" : nas_path/"template/brown_ramen_von_2/0",
    "red_ramen_von_2" : nas_path/"template/red_ramen_von_2/0",
    "yellow_ramen_von_2" : nas_path/"template/yellow_ramen_von_2/0"
}

name2prompt = {
    "pringles" : "pringles",
    "brown_ramen_von_2" : "brownramen",
    "red_ramen_von_2" : "redramen",
    "yellow_ramen_von_2" : "yellowramen",
}

prompt2name = {value:key for key, value in name2prompt.items()}

conda activate flir_python
cd paradex_processing

NAS_PATH='demo_data' python3 multiview_template2tracking/tracking_w_loftr_multiobjs.py --scene_path demo_data/data/input/multi_ramen/0 --obj_names "brown_ramen_von_2" "red_ramen_von_2" "yellow_ramen_von_2" --vis_final
