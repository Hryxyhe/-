# 总结代码调试时的经验
* ①model里面设置'find_unused_parameters=True'可以忽略掉模型的未参与训练参数。但'建议直接手动去除未使用参数'，这时系统会提示find_unused_parameters=True是多于操作，并没有找到未使用参数。
  
* ②模型推理时'不使用梯度可以大幅度减小显存'： 在模型推理时，可以将 PyTorch 模型设为评估模式，并使用 'torch.no_grad()' 上下文管理器，以确保在推理时不计算梯度。这样可以减少显存的使用。
```python
with torch.no_grad():
    model.eval()
    #你的推理代码...>
```


