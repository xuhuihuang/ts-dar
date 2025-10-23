Tutorials
===========

Jupyter notebook examples
*************************

.. raw:: html

   <table>
        <tr>
            <td>
                <a href="../_example/muller-example/muller-example.html">
                    <strong>Example on muller potential</strong>
                    <img src="../_static/muller.png" alt="Thumbnail" class=gallery-image, width="250", height="250">
                    <br>
                </a>
            </td>
            <td>
                <a href="../_example/quadruple-well-example/quadruple-well-example.html">
                    <strong>Example on quadruple-well potential</strong>
                    <img src="../_static/quadruple-well.png" alt="Thumbnail" class=gallery-image, width="250", height="250">
                    <br>
                </a>
            </td>
         <tr>
    </table>


Start with python script
************************

.. code-block:: bash

    python ./ts-dar/scripts/train_tsdart.py \
        --seed 1 \
        --device 'cpu' \
        --lag_time 10 \
        --encoder_sizes 2 20 20 20 10 2 \
        --feat_dim 2 \
        --n_states 2 \
        --beta 0.01 \
        --gamma 1 \
        --proto_update_factor 0.5 \
        --scaling_temperature 0.1 \
        --learning_rate 0.001 \
        --pretrain 10 \
        --n_epochs 20 \
        --train_split 0.9 \
        --train_batch_size 1000 \
        --data_directory ./ts-dar/data/quadruple-well \
        --saving_directory . 

Or

.. code-block:: bash

    sh ./ts-dar/scripts/train_tsdart.sh
