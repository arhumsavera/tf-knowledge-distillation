# Knowledge Distillation - Tensorflow

This is an implementation for the basic idea behind Hinton's [Knowledge Distillation Paper][1]. 

The .py code generates soft targets from the teacher in an on-line manner while training the student network. The Provided notebook implements this in keras as well to make things easier.


### Running the code

Train the Teacher Model

     python main.py --model_type teacher --checkpoint_dir teachercpt --num_steps 5000 --temperature 5
     
Train the Student Model (in a standalone manner for comparison)

     python main.py --model_type student --checkpoint_dir studentcpt --num_steps 5000
     
Train the Student Model (Using Soft Targets from the teacher model)

     python main.py --model_type student --checkpoint_dir studentcpt --load_teacher_from_checkpoint true --load_teacher_checkpoint_dir teachercpt --num_steps 5000 --temperature 5
     
### Results (For different temperature values)

| Model        | Accuracy - 2  | Accuracy - 5 |
| -------------|:-------------:| -------------|  
| Teacher Only | 97.9          | 98.12        |      
| Distillation | 89.14         |  90.77       |  
| Student Only | 88.84         | 88.84        | 

The small model when trained without the soft labels always use **temperature**=1.

### References

[Distilling the Knowledge in a Neural Network](https://arxiv.org/abs/1503.02531)





[1]: https://arxiv.org/abs/1503.02531