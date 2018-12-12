---
title: How can I use AnyWave for reviewing continuous data?
tags: [anywave]
---

# How can I use AnyWave for reviewing continuous data?

AnyWave is a free, multi-platform software that can be used to visualize electrophysiological data, as well as being used as a development framework in order to build custom plug-ins. It is implemented in C++ and available for Windows, Linux and macOS. The graphics of AnyWave is much faster than **[ft_databrowser](/reference/ft_databrowser)** or MATLAB figure sin general, which is especially valuable if you have many channels and/or a very high sampling rate.

You can export data that has been processing in FieldTrip to a format that Anywave understands, such as the BrainVision .vhdr format, review the data in AnyWave, and import the marked time windows back into MATLAB.

    % start with the normal preprocessing of your data
    cfg = ...
    data = ft_preprocessing(cfg);


    filename = 'data.vhdr';
    dat = ft_fetch_data(data);
    hdr = ft_fetch_header(data);

    ft_write_data(filename, dat, 'header', hdr);

After writing the data to disk, you open AnyWave, read the data and mark the time windows of interest.