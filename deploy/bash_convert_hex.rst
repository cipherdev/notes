Bash Convert Hexa
====================

Script:
-------

.. code-block:: kea

    #!/bin/bash
    num=0
    for ((num=0; num<=255; num++))
    do
        reg=$(printf '%x\n' $num)
        echo "+++++ reg=0x$reg +++++"
        ipmitool raw 0x3c 0x17 0x00 0x$reg
        sleep 1
    done

