# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 황성연
- 리뷰어 : 박찬영


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 중요! 해당 조건을 만족하는 부분을 캡쳐해 근거로 첨부
          <img width="1452" height="717" alt="image" src="https://github.com/user-attachments/assets/f4bbd2b5-3b24-48a0-9d87-26e2d0f7e7bd" />

    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭을 왜 핵심적이라고 생각하는지 확인
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드의 기능, 존재 이유, 작동 원리 등을 기술했는지 확인
    - 주석을 보고 코드 이해가 잘 되었는지 확인  
      <img width="904" height="593" alt="image" src="https://github.com/user-attachments/assets/c6d4180d-cd7d-4b72-9fa1-af193e0f28f5" />

        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 프로젝트 평가 기준에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부  
        ```
        import matplotlib.pyplot as plt

# 시각화 설정 (2행 3열: 상단 Loss / 하단 Accuracy)
fig, axes = plt.subplots(2, 3, figsize=(22, 12))
epochs = range(1, EPOCHS + 1)

# 공통 스타일 설정
color_34_orig = '#1f77b4'  # 파란색 (34 Original)
color_34_abl  = '#ff7f0e'  # 주황색 (34 Ablation)
color_50_orig = 'green'    # 초록색 (50 Original)
color_50_abl  = '#d62728'  # 빨간색 (50 Ablation)

style_34 = '-'  # 실선
style_50 = '--' # 점선

# ---------------------------------------------------------
# [가설 1 검증] ResNet-34: Shortcut 유무 집중 비교
# ---------------------------------------------------------
# (0,0) Loss
axes[0, 0].plot(epochs, all_results["ResNet-34 (Original)"]["train_loss"], label="34 Original", color=color_34_orig, linestyle=style_34, linewidth=2)
axes[0, 0].plot(epochs, all_results["ResNet-34 (No Shortcut)"]["train_loss"], label="34 Ablation", color=color_34_abl, linestyle=style_34, linewidth=2)
axes[0, 0].set_title('H1: Loss (34-layer Only)', fontsize=13, fontweight='bold')
axes[0, 0].legend()

# (1,0) Accuracy
axes[1, 0].plot(epochs, all_results["ResNet-34 (Original)"]["val_acc"], label="34 Original", color=color_34_orig, linestyle=style_34, linewidth=2)
axes[1, 0].plot(epochs, all_results["ResNet-34 (No Shortcut)"]["val_acc"], label="34 Ablation", color=color_34_abl, linestyle=style_34, linewidth=2)
axes[1, 0].set_title('H1: Accuracy (34-layer Only)', fontsize=13, fontweight='bold')
axes[1, 0].set_ylabel('Accuracy (%)')
axes[1, 0].legend()

# ---------------------------------------------------------
# [가설 2 검증] 전 모델 비교: 층이 깊어질수록 커지는 쇼트컷의 영향력
# ---------------------------------------------------------
# (0,1) Loss - 4개 선 모두 출력
for i, (name, history) in enumerate(all_results.items()):
    line_style = style_34 if "34" in name else style_50
    line_color = [color_34_orig, color_34_abl, color_50_orig, color_50_abl][i]
    axes[0, 1].plot(epochs, history['train_loss'], label=name, color=line_color, linestyle=line_style, linewidth=2)
axes[0, 1].set_title('H2: Loss (All Models)', fontsize=13, fontweight='bold')
axes[0, 1].legend(fontsize='small')

# (1,1) Accuracy - 4개 선 모두 출력
for i, (name, history) in enumerate(all_results.items()):
    line_style = style_34 if "34" in name else style_50
    line_color = [color_34_orig, color_34_abl, color_50_orig, color_50_abl][i]
    axes[1, 1].plot(epochs, history['val_acc'], label=name, color=line_color, linestyle=line_style, linewidth=2)
axes[1, 1].set_title('H2: Accuracy (All Models)', fontsize=13, fontweight='bold')
axes[1, 1].legend(fontsize='small')

# ---------------------------------------------------------
# [가설 3 검증] 34 Original vs 50 Original: 체급 및 데이터 규모
# ---------------------------------------------------------
# (0,2) Loss
axes[0, 2].plot(epochs, all_results["ResNet-34 (Original)"]["train_loss"], label="34 Original", color=color_34_orig, linestyle=style_34, linewidth=2.5)
axes[0, 2].plot(epochs, all_results["ResNet-50 (Original)"]["train_loss"], label="50 Original", color=color_50_orig, linestyle=style_50, linewidth=2.5)
axes[0, 2].set_title('H3: Loss (34 vs 50 Original)', fontsize=13, fontweight='bold')
axes[0, 2].legend()

# (1,2) Accuracy
axes[1, 2].plot(epochs, all_results["ResNet-34 (Original)"]["val_acc"], label="34 Original", color=color_34_orig, linestyle=style_34, linewidth=2.5)
axes[1, 2].plot(epochs, all_results["ResNet-50 (Original)"]["val_acc"], label="50 Original", color=color_50_orig, linestyle=style_50, linewidth=2.5)
axes[1, 2].set_title('H3: Accuracy (34 vs 50 Original)', fontsize=13, fontweight='bold')
axes[1, 2].legend()

# 공통 레이블 및 레이아웃 정리
for ax in axes.flat:
    ax.set_xlabel('Epochs')
    ax.grid(True, alpha=0.3)

plt.suptitle('ResNet Ablation Study: Comprehensive Verification with 6-Panel Analysis', fontsize=18, fontweight='bold', y=0.98)
plt.tight_layout(rect=[0, 0.03, 1, 0.95])
plt.show()
```
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
<img width="1437" height="525" alt="image" src="https://github.com/user-attachments/assets/9f3cc02d-9b12-4678-89a5-dc5baa959a42" />

        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화/모듈화했는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부  
<img width="471" height="154" alt="image" src="https://github.com/user-attachments/assets/109b98fa-18f7-4f27-838d-6c1bfa8b9a88" />



# 회고(참고 링크 및 코드 개선)
```
굉장히 자세하게 코드를 작성하였고, 각 부분을 이해하기 쉽게 설명하였습니다.
또한 기존 프로젝트에 그치는 것이 아니라, 따로 개인 실험까지 하는 열정까지 보여주셔서 굉장히 흥미롭게 봤습니다.

```
