---
title: "ETKDGv3로 conformer 생성하기"
date: 2026-06-16
tags: [rdkit, cheminformatics]
---

오늘 RDKit `ETKDGv3`로 3D conformer 뽑는 거 정리. 매일 이런 식으로 한 줄이라도 남기는 게 목표.

## 핵심

ETKDG는 distance geometry에 실험적 토션 각도 분포를 얹은 방법이고, v3는 매크로사이클/소분자 모두 안정적이다.

```python
from rdkit import Chem
from rdkit.Chem import AllChem

mol = Chem.MolFromSmiles("CC(=O)Oc1ccccc1C(=O)O")  # aspirin
mol = Chem.AddHs(mol)

params = AllChem.ETKDGv3()
params.randomSeed = 42
AllChem.EmbedMolecule(mol, params)
AllChem.MMFFOptimizeMolecule(mol)

Chem.MolToMolFile(mol, "aspirin_3d.sdf")
```

## 메모

- `AddHs` 안 하고 embed 하면 수소 없이 좌표가 잡혀서 MMFF 최적화가 이상해진다. 꼭 먼저.
- 여러 conformer 필요하면 `EmbedMultipleConfs(mol, numConfs=N, params=params)`.
- seed 고정하면 재현 가능 — 디버깅할 때 필수.

> 코드 블록, 표, 인용 다 마크다운으로 그냥 쓰면 된다. 이미지는 `![설명](경로)`.
