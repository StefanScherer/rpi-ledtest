# ledtest

## Installation

Install pipenv package manager

    pip install --user pipenv

Allow GPIO access from Python scripts without sudo

    sudo chown root $(pipenv run which python)
    sudo chmod 4755 $(pipenv run which python)

## Run the program

    pipenv run python strandtest.py -c
