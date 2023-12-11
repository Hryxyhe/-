# 总结代码调试时的经验
* ①model里面设置find_unused_parameters=True,可以忽略掉模型的未参与训练参数。但建议是注释掉项目里导入但没有用到的block和分支，直接手动去除未使用参数，这时系统会提示find_unused_parameters=True是多于操作，并没有找到未使用参数。
* 模型推理时不使用梯度： 在模型推理时，可以将 PyTorch 模型设为评估模式，并使用 torch.no_grad() 上下文管理器，以确保在推理时不计算梯度。这样可以减少显存的使用。
* `<hpython
Copy code
with torch.no_grad():
    model.eval()
    # 推理代码...>`


