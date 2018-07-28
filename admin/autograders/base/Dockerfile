FROM gradescope/auto-builds:ubuntu-18.04

RUN apt-get update
RUN apt-get install -y python3-pip
RUN pip3 install --upgrade pip
RUN pip3 install pipenv

COPY autograders/base/run_autograder /autograder/

WORKDIR /autograder/source
COPY Pipfile .
COPY Pipfile.lock .
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8
RUN pipenv install --dev --deploy --system --keep-outdated

COPY data/processed data/processed

COPY autograders/base/run_tests.py .