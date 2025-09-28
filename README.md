# for_pa

1. paradex_processing 다운받기
2. cp -r ../shared_data/202510_demo demo_data
3. obj_output --> obj_output_old
4. cp ../shared_data/202510_demo/efficient_sam_s_gpu.jit utils/
5. mkdir checkpoint
   cp ../shared_data/202510_demo/checkpoint/best_v2.pt checkpoint/
   cp -r ../shared_data/202510_demo/paradex_processing/thirdparty .
6. default_config.py 아래처럼 고치기

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

7. conda activate flir_python
8. NAS_PATH='demo_data' python3 multiview_template2tracking/tracking_w_loftr_multiobjs.py --scene_path demo_data/data/input/multi_ramen/0 --obj_names "brown_ramen_von_2" "red_ramen_von_2" "yellow_ramen_von_2" --vis_final
