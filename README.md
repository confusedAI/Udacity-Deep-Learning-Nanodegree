# Coding Assignment for ServiceNow
Some of the limitations or tasks I could not complete in the below code:
1. Although I am using the accelerate package for model parallelism the code was tested on a single T4 GPU available on GCP.
2. **For Task 9:** Adjust dependent layers is not completed.

3. **For Task11:** Training is only done on 8K samples from squad['train']. Due to limited time availability in Google Colab, the data was cut short but the training code will work for the whole data also. The same goes for evaluation, done only on 1K samples.</br>
**Implications:** The newly trained model won't see all contexts in the train data since context repeats a lot in the SQuAD dataset with different questions.

4. The train data and validation data were stored on the list rather than a numpy array. Lists are computationally expensive in terms of space reducing batch-size.

5. **For Task 12:** I used the F1 score(%) as the evaluation metric which is token overlap between the predicted answer and the reference answer.</br>
   **Pitfall** of using F1 score: F1 score is sensitive to exact matches between predicted and reference answers. If the model provides an answer that is semantically correct but not exactly matched with the reference answer, the F1 score will penalize it.

6. Did not create a separate conda environment for the code to be portable. Directly used the Google Colab notebook which provides pre-installed packages like hugging-face, pytorch, etc.
