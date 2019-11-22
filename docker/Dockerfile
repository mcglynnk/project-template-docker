# base image
FROM continuumio/miniconda3:4.6.14

# load in the environment.yml file
ADD ./docker/environment.yml /

# create the environment
COPY environment.yml environment.yml
RUN conda env update -f environment.yml && conda clean --all -y

#RUN conda update -n base -c defaults conda && conda create -n testenv && conda env update && conda clean -a -y
#RUN conda update -n testenv conda -y && conda env update


# add the code folder and notebooks folder to the docker image - this allows us to run
# the image directly without relying on docker-compose or local file dependenciess
ADD ./code_/ /code_
ADD ./notebooks /notebooks

ENTRYPOINT ["tini", "-g", "--"]